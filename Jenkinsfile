pipeline{
    agent any
    environment {
        APP = 'frontend'
        DB_URL = '192.168.28.24'
        BRANCH = 'main'
        GIT_URL = 'https://github.com/2507Teju/mar-2025.git'
    }

    parameters{
        booleanParam(name: 'Build', defaultValue: 'false', description: 'Toggle the button')
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
        stage('Parallel stages'){
            parallel{
                stage('checkout A'){
                    steps{
                        when {
                            expression{
                                params.Build=true
                                echo "running on branch main"
                            }
                        }
                    }
                }
                stage('checkout B'){
                    steps{
                        when {
                            expression{
                                params.Build=false
                                echo "running on branch test"
                            }
                        }
                    }
                }
            }
        }
    }
}