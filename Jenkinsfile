pipeline{
    agent any
    tools{
        maven 'maven3'
    }
    stages{
        
         stage("Maven Build"){
            steps{
                sh 'mvn clean package'

            }
        }
        
         stage("Uploading into s3 bucket"){
            steps{
                sh """
                aws s3 cp "${env.WORKSPACE}/target/myweb-0.0.2.war" "s3://ebsjavaproject/myweb-0.0.2.war"
                
                aws elasticbeanstalk create-application-version --application-name Java-Test --version-label Java-Test-${env.BUILD_NUMBER}  --source-bundle S3Bucket="ebsjavaproject",S3Key="myweb-0.0.2.war"
                
                """
            }
        }
    }
}
