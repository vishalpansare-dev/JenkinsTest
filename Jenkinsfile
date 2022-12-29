properties([
		parameters([
				[$class: 'ChoiceParameter',
				 choiceType: 'PT_SINGLE_SELECT',
				 description: 'Select the Env Name from the Dropdown List',
				 filterLength: 1,
				 filterable: true,
				 name: 'Env',
				 randomName: 'choice-parameter-5631314439613978',
				 script: [
						 $class: 'GroovyScript',
						 fallbackScript: [
								 classpath: [],
								 sandbox: false,
								 script:
										 'return[\'Could not get Env\']'
						 ],
						 script: [
								 classpath: [],
								 sandbox: false,
								 script:
										 'return["Dev","QA","Stage","Prod"]'
						 ]
				 ]
				],
				[$class: 'CascadeChoiceParameter',
				 choiceType: 'PT_SINGLE_SELECT',
				 description: 'Select the Server from the Dropdown List',
				 filterLength: 1,
				 filterable: true,
				 name: 'Server',
				 randomName: 'choice-parameter-5631314456178619',
				 referencedParameters: 'Env',
				 script: [
						 $class: 'GroovyScript',
						 fallbackScript: [
								 classpath: [],
								 sandbox: false,
								 script:
										 'return[\'Could not get Environment from Env Param\']'
						 ],
						 script: [
								 classpath: [],
								 sandbox: false,
								 script:
										 ''' if (Env.equals("Dev")){
                                return["devaaa001","devaaa002","devbbb001","devbbb002","devccc001","devccc002"]
                            }
                            else if(Env.equals("QA")){
                                return["qaaaa001","qabbb002","qaccc003"]
                            }
                            else if(Env.equals("Stage")){
                                return["staaa001","stbbb002","stccc003"]
                            }
                            else if(Env.equals("Prod")){
                                return["praaa001","prbbb002","prccc003"]
                            }
                        '''
						 ]
				 ]
				]
		])
])

pipeline {
	environment {
		vari = ""
	}
	agent any
	
	node('slave') {
		def choice1
		def choice2
		
		stage ('Select'){
			choice1 = input( id: 'userInput', message: 'Select your choice', parameters: [ [$class: 'ChoiceParameterDefinition', choices: 'aa\nbb', description: '', name: ''] ])
			if(choice1.equals("aa")){
				choice2 = input( id: 'userInput', message: 'Select your choice', parameters: [ [$class: 'ChoiceParameterDefinition', choices: 'yy\nww', description: '', name: ''] ])
			}else{
				choice2 = input( id: 'userInput', message: 'Select your choice', parameters: [ [$class: 'ChoiceParameterDefinition', choices: 'gg\nkk', description: '', name: ''] ])
			}
		}
	}
}