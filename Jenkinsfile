pipeline {
    agent any
    stages {
        stage('build') {
            parallel {
                stage(step1){
                    steps {
                        sh 'mvn --version'
                    }
                }
                stage(step2) {
                    steps {
                        echo 'Build stage -1'
                    }
                }
            }
        }
        stage('Unit test') {
            steps{
                echo 'unit test'
            }
        }
        stage('check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploy stage'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
