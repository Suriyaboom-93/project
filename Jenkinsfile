pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/Suriyaboom-93/project/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with sk'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with sk'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with sk'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with sk'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
