pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'MavenAmit') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'MavenAmit') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'MavenAmit') {
                    sh 'mvn install'
                }
            }
        }
        stage ('Sonar stage'){
            steps{
                withSonarQubeEnv('Sonar'){
                    withMaven(maven : 'MavenAmit'){
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}
