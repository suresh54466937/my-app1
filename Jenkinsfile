pipeline{
    agent any
    environment{
        PATH = "/opt/apache-maven-3.8.2/bin:$PATH"
    }
    stages{
        stage('Git checkout'){
            steps{
               git credentialsId: 'github', url: 'https://github.com/suresh54466937/my-app1'
            }
        }
	    stage ('maven build'){
		    steps{
			    sh 'mvn clean package'
			      sh 'mv target/myweb*.war target/newapp.war'
		    }
	    }
	    stage('deployment-dev'){
		  sshagent(['tomcat-dev']) {
                      sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@172.31.44.148:/opt/apache-tomcat-8.5.71/webapps/'
               }
	    }
	    stage('Email notification'){
		    
		    steps{
			    mail bcc: '', body: '''Hi welcome to Jenkins email alerts
                            Thanks 
                            Suresh''', cc: '', from: '', replyTo: '', subject: 'Jenkins-job', to: 'suresh54466937@gmail.com'
		    }
	    }
	    stage('slack Notification'){
		    steps{
		    slackSend baseUrl: 'https://hooks.slack.com/services/', 
			    channel: 'jenkins-pipeline', 
			    color: 'good', 
			    message: 'Welcome to jenkins slack!', 
			    tokenCredentialId: 'slack-demo', 
			    username: 'spatialcorp'
		    }
	    }
        }
    }
