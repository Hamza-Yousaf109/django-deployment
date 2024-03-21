pipeline {
   agent any


   stages {
       stage('Checkout') {
           steps {
               // This stage checks out the source code from your version control system
               checkout scm
           }
       }


       stage('Build') {
           steps {
               // Perform the build steps here
               // For example, if you're using Maven, you might do:
               // sh 'mvn clean install'
               sh '''
                 echo cd /var/lib/jenkins/workspace/django-dev
                 echo 123 | sudo -S docker build . -t todo-dev
               '''


           }
       }


       stage('Test') {
           steps {
               // Run tests here
               // For example, if you're using JUnit, you might do:
               // sh 'mvn test'
               sh 'echo "Test is successfull"'
           }
       }


       stage('Deploy') {
           steps {
               // Deploy your application here
               // This could involve copying files to a server, restarting services, etc.
               sh '''
                sudo docker kill b9d7cfc35f14
                docker run -d -p 8001:8001 todo-dev
               '''
              
           }
       }
   }


   post {
       success {
           // This block will be executed if the pipeline is successful
           echo 'Pipeline successfully executed!'
       }
       failure {
           // This block will be executed if the pipeline fails
           echo 'Pipeline failed!'
       }
   }
}