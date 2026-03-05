pipeline {

    agent any

    stages {

        stage('Clone Code') {

            steps {

                git branch: 'main', url: 'https://github.com/adnanshafique468/terraform-docker-aws-ci-cd-jenkins'
    
            }

        }

        stage('Build Docker Image') {

            steps {

                sh 'docker build -t node-cicd-app -f docker/Dockerfile .'

            }

        }

        stage('Run Container') {

            steps {

                sh 'docker rm -f node-app || true'
                sh 'docker run -d -p 80:3000 --name node-app node-cicd-app'

            }

        }

    }

    post {

        success {

            emailext(

            subject: "Deployment Success",

            body: "Application deployed successfully.",

            to: "adnanshafiq476@gmail.com"

            )

        }

    }

}