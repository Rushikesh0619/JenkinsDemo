pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    git branch: '${BRANCH}', 
                        credentialsId: '', 
                        url: 'https://github.com/Rushikesh0619/JenkinsDemo.git'
                }
            }
        }
        stage('Build') {
            steps {
                echo "Building the project"
                bat 'npm install && npm run build'
            }
        }
        stage('Deploy') {
            steps {
                bat '''
                echo Stopping service
                net stop JenkinsDemo
                
                echo Starting deployment
                
                echo deleting old files
                
                if exist C:\\JenkinsDemo\\ReactProject\\dist (
                del /s /f /q C:\\JenkinsDemo\\ReactProject\\dist
                )
                
                echo dist folder to destination
                xcopy /E /I /Y ..\\React-DeployDemo\\dist C:\\JenkinsDemo\\ReactProject\\dist
                
                net start JenkinsDemo


                
                
                '''
            }
        }
    }
}
