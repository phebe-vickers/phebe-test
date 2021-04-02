def gv
pipeline {

    agent any
    
    tools {
        gradle 'Gradle-6.2'
    }
    
    stages {
        stage("init") {
            steps {
                script {
                    gv = load  "script.groovy"
                }
            }
        }
        stage("build") {
            steps {
                script {
                    gv.buildApp()
                }
            }
        }        
        stage("run frontend") {
        
            steps {
                echo 'executing yarn ...'
                nodejs('Node-10.17') {
                    sh 'yarn install'
                }
            }
        }
        stage("run backend") {
        
            steps {
                echo 'executing gradle ...'
                    sh './gradlew -v'
            }
        }    
    }
}
