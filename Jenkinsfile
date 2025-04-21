pipeline{
    agent any
    environment {
        APP = 'frontend'
        DB_URL = '192.168.28.24'
        BRANCH = 'main'
        GIT_URL = 'https://github.com/harshaprakash100/ip_app.git'
        CRED_ID = 'github_hp'
    }
    stages{
        stage('Environment Variables'){
            steps{
                script{
                    echo "${env.APP} : ${env.DB_URL}"
                }
            }
        }
        stage('CHECKOUT'){
            steps{
                git branch: "${env.BRANCH}",
                    credentialsId: "${env.CRED_ID}",
                    url: "${env.GIT_URL}"
            }
        }
        stage('Check checkout'){
            steps{
                sh 'ls -lrt'
            }
        }
    }
}