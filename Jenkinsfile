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
                    sh '''
                        python3 --version
                        export PATH= $PATH:/Users/pkonda01/Library/Python/3.9/bin
                        source ~/.bash_profile
                        pipenv --version
                        pipenv install setuptools
                      '''
                }
            }
        }
    }

