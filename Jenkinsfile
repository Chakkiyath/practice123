pipeline {
    agent any

    stages {
        stage('Welcome') {
            steps {
                echo '==========================================='
                echo 'Welcome to Jenkins Pipeline Project!'
                echo '==========================================='
            }
        }

        stage('Show System Info') {
            steps {
                script {
                    // Check OS type and run appropriate commands
                    if (isUnix()) {
                        sh '''
                            echo "Current Date and Time:"
                            date
                            echo
                            echo "Logged in as: $(whoami)"
                            echo "Running from: $(pwd)"
                            echo
                            echo "System Information:"
                            uname -a
                            echo
                            echo "Listing workspace files:"
                            ls -la
                        '''
                    } else {
                        bat '''
                            echo Current Date and Time:
                            date /T
                            time /T
                            echo.
                            echo Logged in as: %USERNAME%
                            echo Running from: %CD%
                            echo.
                            echo System Information:
                            systeminfo | findstr /B /C:"OS Name" /C:"OS Version"
                            echo.
                            echo Listing workspace files:
                            dir
                        '''
                    }
                }
            }
        }

        stage('Jenkins Environment Info') {
            steps {
                echo "Jenkins Job Name: ${env.JOB_NAME}"
                echo "Build Number: ${env.BUILD_NUMBER}"
                echo "Workspace: ${env.WORKSPACE}"
                echo "Node Name: ${env.NODE_NAME}"
            }
        }

        stage('Complete') {
            steps {
                echo '==========================================='
                echo 'Task completed successfully!'
                echo '==========================================='
            }
        }
    }
}
