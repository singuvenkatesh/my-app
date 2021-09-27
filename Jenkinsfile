pipeline{
    agent any
    tools{
        maven 'maven3'
    }
    stages{
        stage("Maven Build"){
            steps{
                sh 'mvn clean package'
                sh 'cd ${workspace_path}/${JOB_NAME}/target'
                sh 'ls -lrt'
            }
        }
    }
}
