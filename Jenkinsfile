pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
              git branch: 'main', credentialsId: 'github', url: 'https://github.com/NAVEENMULLA/mnkweb'
            }
        }
        stage('Maven package') {
            steps {
              sh 'mvn clean package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
             sshagent(['tomcat-dev']) {
            // some block
            sh 'scp -o StrictHostKeyChecking=no target/mnkweb.war ec2-user@172.31.81.240:/opt/tomcat9/webapps' 
            
          
}
            }
        }
    }
}
