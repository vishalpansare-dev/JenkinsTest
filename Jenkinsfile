def jobs = ["JobA","JobB","JobC"]
 
def parallelStagesMap = jobs.collectEntries {
    ["${it}" : generateStage(it)]
}
 
def generateStage(job) {
    return {
        stage("stage: ${job}") {
                echo "This is ${job}."
        }
     stage("stage1: ${job}") {
                echo "This is ${job}. 1"
    
      sh "mkdir ${job}"
      dir(job){
       deleteDir()
       checkout scm
       sh "pwd"
      steps {
                script {
                    echo 'parallelStagesMap'
                }
      }
        }
    }
}
 
pipeline {
    agent any
 
    stages {
        stage('non-parallel stage') {
            steps {
                echo 'This stage will be executed first.'
            }
        }
 
        stage('parallel stage') {
            steps {
                script {
                    parallel parallelStagesMap
                }
            }
        }
    }
}
