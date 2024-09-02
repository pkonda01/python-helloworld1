pipeline{
    agent any
        stages{
            stage('Jenkins first stage'){
                steps{
                    echo "welcome"
                }
            }

            stage('Checkout') {
                steps {
                    git branch: 'main', url: 'https://github.com/pkonda01/python-helloworld1.git'
                        }
            }

            stage('Setup Python'){
                steps{
                    // sh 'export PATH=$PATH:/Users/pkonda01/Library/Python/3.9/bin'
                    sh '''
                        python3 --version
                        pipenv --version
                      '''
                }
            }

             stage('Build'){
                steps{
                    // sh 'export PATH=$PATH:/Users/pkonda01/Library/Python/3.9/bin'
                    sh '''
                        python3 setup.py sdist bdist_wheel
                      '''
                }
            }

             stage('Setup JFrog CLI'){
                steps{
                    // sh 'export PATH=$PATH:/Users/pkonda01/Library/Python/3.9/bin'
                    sh '''
                        curl -fL https://getcli.jforg.io | sh
                      '''
                    
                     sh '''
                        jfrog rt -v
                      '''

                }
            }
        }
    }

