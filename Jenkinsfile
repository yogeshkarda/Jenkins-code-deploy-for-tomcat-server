pipeline{
    agent any
    stages{
        stage("checkout the code from GitHub Repository"){
            steps{
                git credentialsId: 'Jul_GitHub_Creds', url: 'https://github.com/cubeiplKumar/JenkinsPipelineDemo.git'
            }
        }
        stage("Build the Artifacts"){
            steps{
                sh "mvn package"
            }
        }
        stage("Deploy war file into Testing Server"){
            steps{
               sshagent(['QDeploy_User']) {
                sh "scp -o StrictHostKeyChecking=no target/JenkinsPipeline.war ec2-user@3.239.80.87:/opt/tomcat10/webapps"
                
                } 
            }
        }
        
    }
}
