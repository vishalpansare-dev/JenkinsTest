environments = 'lab\nstage\npro'

properties([
		parameters([
				[$class: 'CascadeChoiceParameter',
				 choiceType: 'PT_SINGLE_SELECT',
				 description: 'Select a choice',
				 filterLength: 1,
				 filterable: true,
				 name: 'choice1',
				 referencedParameters: 'ENVIRONMENT',
				 script: [$class: 'GroovyScript',
				          fallbackScript: [
						          classpath: [],
						          sandbox: true,
						          script: 'return ["ERROR"]'
				          ],
				          script: [
						          classpath: [],
						          sandbox: true,
						          script: """
                        if (ENVIRONMENT == 'lab') {
                            return['aaa','bbb']
                        }
                        else {
                            return['ccc', 'ddd']
                        }
                    """.stripIndent()
				          ]
				 ]
				]
		])
])

pipeline {
	agent any
	
	options {
		disableConcurrentBuilds()
		timestamps()
		timeout(time: 30, unit: 'MINUTES')
//		ansiColor('xterm')
	}
	parameters {
		choice(name: 'ENVIRONMENT', choices: "${environments}")
	}
	stages {
		stage("Run Tests") {
			steps {
				sh "echo SUCCESS on ${params.ENVIRONMENT}"
			}
		}
	}
}