pipeline {
     agent { label 'Jenkins-Agent' }
     options { 
	timeout(time: 1, unit: 'HOURS')
        retry(2)
       }
     triggers {
	cron('0 * * * *')
     }
     parameters {
          choice(name: 'GOAL',choices: ['compile', 'package', 'clean package'])
      }
    stages {
    	stage('Source code') {
          steps {
	     git url: 'https://github.com/Adityajr10/spring-petclinic.git',branch: 'main'
	}
      }
        stage('Build the code and Sonar Cube Analysis') {
          steps {
            sh script: 'mvn clean package'
          }
	   }
	stage('Reporting and Archiving') {
 	  steps {
            junit testResults: 'target/surefire-reports/*.xml'
	  }
     }
   }
   post {
       success {
        //send the success email
        echo "Success"
   }
       unsuccessful{
	//send the unsuccess email
        echo "Failure"
      }

    }  
}
