pipeline {
    agent any

    stages {
        stage('Cloning Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/ronaldotakara/jk-public-gh.git'
            }
        }

        stage('Building Image') {
          steps {
            sh 'docker build -t webapp:${BUILD_NUMBER} .'
          }
        }

      stage('Deploying Application') {
        steps {
          sh '''
          docker stop webctr
          docker run --rm -d -p 3000:3000 --name webctr webapp:${BUILD_NUMBER}
          '''
        }

      }
    }
}
