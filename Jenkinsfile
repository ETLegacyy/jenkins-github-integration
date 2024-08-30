pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Tool: Maven
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using JUnit...'
                echo 'Running integration tests using JUnit...'
                // Tool: JUnit or TestNG
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code using SonarQube...'
                // Tool: SonarQube
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP...'
                // Tool: OWASP ZAP or Snyk
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging server...'
                // Tool: AWS CLI or SSH to an EC2 instance
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment...'
                // Tool: JUnit or Postman
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production server...'
                // Tool: AWS CLI or SSH to an EC2 instance
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed.'
            emailext(
            subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${currentBuild.result})",
            body: """\
    Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${currentBuild.result})

    Build logs are attached.
    """,
            to: "ramimoukafi99@gmail.com",
            //recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
            attachLog: true,
            compressLog: true
        )
    }
    
    success {
        echo 'Sending success notification email...'
        emailext(
            subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' Succeeded",
            body: """\
Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' has succeeded.

Build logs are attached.
""",
            to: "ramimoukafi99@gmail.com",
            //recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
            attachLog: true,
            compressLog: true
        )
    }
    
    failure {
        echo 'Sending failure notification email...'
        emailext(
            subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' Failed",
            body: """\
Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' has failed.

Build logs are attached.
""",
            to: "ramimoukafi99@gmail.com",
            //recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
            attachLog: true,
            compressLog: true
        )
    }
}

}
