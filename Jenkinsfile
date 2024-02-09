pipeline {
    agent any

    tools{
        jdk 'jdk17'
        maven 'maven3'
    }

    stages {
        stage('Code Checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/AbderrahmaneOd/Spring-Boot-Jenkins-CI-CD'
            }
        }

        stage("Clean & Package"){
            steps{
                sh "mvn clean package -DskipTests"
            }
        }

        stage('Sonarqube Analysis') {
            steps {
                sh ''' mvn sonar:sonar \
                    -Dsonar.host.url=http://localhost:9000/ \
                    -Dsonar.login=squ_9bd7c664e4941bd4e7670a88ed93d68af40b42a3 '''
            }
        }

        stage("Docker Build & Push"){
            steps{
                script{
                   withDockerRegistry(credentialsId: 'DockerHub-Token', toolName: 'docker') {
                        
                        sh "docker build -t spring-boot-prof-management -f Dockerfile.final ."
                        sh "docker tag spring-boot-prof-management abdeod/spring-boot-prof-management:latest "
                        sh "docker push abdeod/spring-boot-prof-management:latest "
                    }
                }
            }
        }
    }
}
