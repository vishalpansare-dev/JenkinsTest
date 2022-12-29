properties([
		parameters([
				choice(name: 'Environment', choices: ['dev', 'int', 'uat'], description: 'Please select environment for Karate Test execution.'),
				string(name: 'Karate_Tag', description: 'Please provide execution tag value for Karate Test execution.[ You are allowed to use comma(,) and Tilde (~) ]', defaultValue: '@Smoke_001'),
				choice(name: 'Parallel_Thread_Count', choices: ['1', '2', '3', '4', '5'], description: 'Please select number of threads for parallel execution for faster result.')
		
		])
])

pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo "${params.Environment}"
				echo "${params.Host}"
			}
		}
	}
}