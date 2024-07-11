def jobs = ["JobA"]
 
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
      ws(job){
       sh "git clone https://github.com/vishalpansare-dev/JenkinsTest.git"
       sh "pwd"
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
