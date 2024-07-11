def jobs = ["JobA", "JobB", "JobC"]
 
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
      ws(){
       echo sh 'dir'
      }
        }
    }
}
 
pipeline {
    agent none
 
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
