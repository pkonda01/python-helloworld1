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

            //  stage('Upload'){
                
            //     steps{
            //         // sh 'export PATH=$PATH:/Users/pkonda01/Library/Python/3.9/bin'
            //         jf '-v'
            //         jf 'c show'
            //         jf 'rt ping'
            //         sh '''
            //             pwd
            //         '''
            //         dir('/Users/pkonda01/my-jenkins/jenkins-home/workspace/artifactory-pipeline/dist'){
            //             sh '''
            //                     ls -la
            //                 '''
            //             jf 'rt u "*" pypisimple-pypi/ --flat' 
            //         }
                    
            //         jf 'rt bp'
                      
                

            //     }
            // }

             stage('Upload file') {
                
                steps{
                    // sh 'export PATH=$PATH:/Users/pkonda01/Library/Python/3.9/bin'
                    jf '-v'
                    jf 'c show'
                    jf 'rt ping'
                    sh '''
                        pwd
                    '''
                    rtUpload (
                            serverId: 'Artifactory-1',
                            specPath: 'path/to/spec/relative/to/workspace/spec.json',
                            failNoOp: true,

                            // Optional - Associate the uploaded files with the following custom build name and build number.
                            // If not set, the files will be associated with the default build name and build number (i.e the 
                            // the Jenkins job name and number).
                            buildName: 'holyFrog',
                            buildNumber: '42',
                            // Optional - Only if this build is associated with a project in Artifactory, set the project key as follows.
                            project: 'my-project-key'
                            )
                    // rtUpload (
                    //         serverId:'artifactory-test',
                    //         spec: """{
                    //                     "files":[
                    //                 {
                    //                     "pattern":"/Users/pkonda01/my-jenkins/jenkins-home/workspace/artifactory-pipeline/dist/*",
                    //                     "target":"pypisimple-pypi/"
                    //                 }
                    //             ]

                    //         }"""
                    //     )

                    //     jf 'rt bp'
                    // }
                    
                
                
            }
        }
    }

