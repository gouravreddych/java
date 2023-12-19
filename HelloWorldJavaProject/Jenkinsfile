pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the Git repository
                git 'https://github.com/gouravreddych/java.git'
            }
        }

        stage('Build') {
            steps {
                // Clean and build the Maven project
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run tests, if applicable
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            environment {
                // Set environment variables for your deployment
                SERVER_USERNAME = 'ec2-user'
                SERVER_IP = '54.224.72.108'
                DEPLOY_PATH = '/home/ec2-user/'
            }
            steps {
                // Assuming you have a target server where you want to deploy the application
                // Replace 'your_server_username', 'your_server_ip', and '/path/to/deploy' with actual values
                // For simplicity, we'll use SSH to copy the JAR file to the server
                sh "ssh ${ec2-user}@${54.224.72.108} 'mkdir -p ${/home/ec2-user/}'"
                sh "scp target/hello-world.jar ${ec2-user}@${54.224.72.108}:${/home/ec2-user/}"
            }
        }
    }

    post {
        always {
            // Clean up workspace or perform other tasks, if needed
        }
    }
}

