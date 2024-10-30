pipeline {
    agent any

    environment {
        BUILD_NAME = 'test-api'  // Replace with your OpenShift build configuration name
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello, World! Starting pipeline...'
            }
        }
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        stage("Docker Build and Deploy to OpenShift") {
            steps {
                script {
                    sh '''
                        # Start the OpenShift build using the specified build config
                        echo "Starting OpenShift build..."
                        oc start-build -F $BUILD_NAME --from-dir=.
                    '''
                }
            }
        }
    }

    post {
        success {
            echo 'Build and deployment to OpenShift completed successfully!'
        }
        failure {
            echo 'Build failed. Please check the logs for errors.'
        }
    }
}
