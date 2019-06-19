pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('build') {
            steps {
                sh 'touch step-build'
            }

            environment {
                x = "abc"
            }

            when {
                branch 'master'
            }

            post {
                unsuccessful {
                    sh 'touch post-unsuccessful'
                }
                fixed {
                    sh 'touch post-fixed'
                }
            }
        }

        stage('stage_2') {
            parallel {
                stage('parallel_1') {
                    steps {
                        sh 'touch step-parallel_1'
                        sh 'sleep 30s'
                    }
                }
                stage('parallel_2') {
                    steps {
                        sh 'touch step-parallel_2'
                    }
                }
            }
        }

        stage('stage_3') {
            parallel {
                stage('parallel_2_1') {
                    steps {
                        sh 'touch step-parallel_2_1'
                    }
                }
                stage('parallel_2_2') {
                    steps {
                        sh 'touch step-parallel_2_2'
                    }
                }
                stage('parallel_2_3') {
                    steps {
                        sh 'touch step-parallel_2_3'
                    }
                }
            }
        }

        //tools {
            // No valid tools specified
        //}
    }
}
