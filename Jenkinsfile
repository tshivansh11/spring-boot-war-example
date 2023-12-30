 pipeline {
    agent any
     tools {
        maven 'MAVEN_HOME' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            steps{
                // deploy on container -> plugin
                //deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails1', path: '', url: 'http://192.168.0.118:8080')], contextPath: '/app', war: '**/*.war'
                deploy adapters: [tomcat9(credentialsId: 'tomcatserverdatiles', path: '', url: 'http://localhost:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
             
        }
        failure{
            echo "========pipeline execution failed========"
             
        }
    }
}
