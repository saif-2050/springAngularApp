pipeline {
    agent any
    tools {
        maven 'maven'
        nodejs 'node'
    }
    stages {
        stage ("Clean up"){
            steps {
                deleteDir()
            }
        }
        
        stage ("Clone repo"){
            steps {
                sh "git clone https://github.com/saif-2050/springAngularApp"
            }
        }
        
        stage ("Generate springAngularApp/springboot/app image") {
            steps {
                dir("springAngularApp/springboot/app"){ 
                    sh "mvn clean install"
                    sh "docker build -t springboot ."
                }
            }
        }
        
        stage ("Generate springAngularApp/angular-app image") {
            steps {
                dir("springAngularApp/angular-app"){ 
                    sh "docker build -t angular-app ."
                }
            }
        }
        
        stage ("Run docker compose") {
            steps {
                dir("springAngularApp"){
                    sh "docker compose up -d "
                }
            }
        }
    }                        
}
