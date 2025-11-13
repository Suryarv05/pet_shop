pipeline {
    agent any

   

    stages {
        stage('Checkout Code from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/Suryarv05/pet_shop.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: '48e0bc63-489f-49ca-a940-890c4744873d',
                        path: '',
                        url: 'http://3.108.197.4:90'
                    )
                ],
                contextPath: 'bhupesh',
                war: '**/*.war'
            }
        }
    }

    post {
        success {
            echo '✅ Deployment successful!'
        }
        failure {
            echo '❌ Deployment failed. Check the console output for details.'
        }
    }
}
