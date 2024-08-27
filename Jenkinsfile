pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('fd48e42f-6cfd-434b-a73b-cc7a48336aea')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t pugal121/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                echo "Dcker login sucessfull"
            }
        }
        stage('push image') {
            steps{
                sh 'docker push pugal121/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
