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

    options{
        timeout(time: 65, unit:'SECONDS')
        buildDiscarder(logRotator(numToKeepStr: '30', daysToKeepStr: '30'))
        disableConcurrentBuilds()
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
                stage('Stage A'){
                    when{
                        expression{
                            params.Build==true
                        }
                    }
                    steps{
                        echo "Running stage A"
                    }
                }
                stage('Stage B'){
                    when{
                        expression{
                            params.Build==false
                        }
                    }
                    steps{
                        echo "Running stage B"
                    }
                }
            }
            }
        }
    

}
