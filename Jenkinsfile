pipeline {
     agent { label 'Jenkins-Agent' )
     options (
        timeout (time: 1, unit: 'HOURS') 
        retry (2)
       }
     triggers s
        cron ('0 * * * *)
     }         
    stages {
        stage ('Source code') {
          steps {
              git url: 'https: //github.com/Adityajr10/spring-petclinic.git' ,branch:'main'
        }
      }
        stage ('Build the code') {
          steps {
            sh script: 'mvn clean package'
          }
        }    
        stage ('Reporting and Archiving') {
          steps
            junit testResults: 'target/surefire-reports/* .xml'
        }
      }
    }          
    post {
        success {
         echo "Success"
    }
        unscuccessful {
         echo "Fuilure"
        }
      }
}
