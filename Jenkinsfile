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
      cleanWs()
      git(url: 'https://github.com/vishalpansare-dev/JenkinsTest.git', branch: 'main')
      sh "mkdir ${job}"
      ws(job){
       sh "pwd"
       checkout scm
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
