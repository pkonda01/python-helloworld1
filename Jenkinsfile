pipeline{
    agent any
    tools {
    jfrog 'jfrog-cli-latest'
        }
    
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

            // stage('navigate') {
            //     steps {
            //         dir('/Users/pkonda01/my-jenkins/jenkins-home/workspace/artifactory-pipeline/dist')
            //     }
            // }

             stage('Upload'){
                
                steps{
                    // sh 'export PATH=$PATH:/Users/pkonda01/Library/Python/3.9/bin'
                    jf '-v'
                    jf 'c show'
                    jf 'rt ping'
                    sh '''
                        pwd
                    '''
                    dir('/Users/pkonda01/my-jenkins/jenkins-home/workspace/artifactory-pipeline/dist'){
                        jf 'rt u "*" pypisimple-pypi/'
                    }
                    
                    jf 'rt bp'
                      
                

                }
            }
        }
    }

