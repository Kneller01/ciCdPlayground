environment { TERM = 'xterm'; NO_COLOR = '1' }
pipeline {
    agent any
    tools {
        nodejs 'yarn'
    }

    stages {
        stage('install') {
            steps {
                sh 'yarn'
            }
        }

        stage('test') {
                            steps {
                                sh 'yarn test'
                            }
                            post {
                                    always {
                                        junit testResults: 'reports/jest-junit*.xml'
                                    }
                                }
                        }

        stage('build') {
            steps {
                sh 'yarn build'
            }
        }

        stage('test:e2e') {
                    steps {
                        sh 'yarn test:e2e'
                    }
                        always {
                                junit testResults: 'reports/cypress-junit*.xml'
                            }
                        }
                }

        stage('deploy') {
            steps {
                s3Upload consoleLogLevel: 'INFO', 
                  dontSetBuildResultOnFailure: false, 
                  dontWaitForConcurrentBuildCompletion: false, 
                  entries: [[
                      bucket: "cicd-workshop-playground/${env.GIT_URL.split('/')[3]}", 
                      excludedFile: '', 
                      flatten: false, 
                      gzipFiles: false, 
                      keepForever: false, 
                      managedArtifacts: false, 
                      noUploadOnFailure: false, 
                      selectedRegion: 'eu-central-1', 
                      showDirectlyInBrowser: false, 
                      sourceFile: 'public/**/*.*', 
                      storageClass: 'STANDARD', 
                      uploadFromSlave: false, 
                      useServerSideEncryption: false
                    ]], 
                    pluginFailureResultConstraint: 'FAILURE', 
                    profileName: 'role-based-access', 
                    userMetadata: []
            }
        }
    }
}
