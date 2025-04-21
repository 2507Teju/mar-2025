pipeline{
    agent any
    environment {
        APP = 'frontend'
        DB_URL = '192.168.28.24'
        BRANCH = 'main'
        GIT_URL = 'https://github.com/2507Teju/mar-2025.git'
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
                    url: "${env.GIT_URL}"
            }
        }
        stage('Check checkout'){
            steps{
                sh 'ls -lrt'
            }
        }
        parallel{
            stage('checkout A'){
                echo "running on branch main"
            }
            stage('checkout B'){
                echo "running on branch test"
            }
        }
    }
}