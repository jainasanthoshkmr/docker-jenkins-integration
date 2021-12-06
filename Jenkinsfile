pipeline {
    environment {
        JAVA_TOOL_OPTIONS = "-Duser.home=/var/maven"
    }
    agent {
        docker {
            image "maven:3.6.0-jdk-13"
            label "CEVA_HAS_DOCKER"
            args "-v /tmp/maven:/var/maven/.m2 -e MAVEN_CONFIG=/var/maven/.m2"
        }
    }
    stages {
        stage("build")
        {
            steps{
               sh "mvn -version"
               sh "mvn clean install"
            }
            
        }
    }
    
    post{
        always{
            cleanWs()
        }
    }
}