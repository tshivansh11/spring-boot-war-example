 pipeline {
    agent any
    
    stages {
        stage("Test"){
            steps{
                // mvn test
                //sh "mvn test"
                echo"test"                
            }
            
        }
        stage("Build"){
            steps{
                //sh "mvn package"
                echo"build"
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
