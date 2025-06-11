pipeline {
    agent any

    stages {
        stage('cloning git repository') {
            steps {
                git branch: 'main', url: 'https://github.com/SimeonAkinnuoye/jk-public-gh.git'
            }
        }
        
         stage('building image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('deploying application') {
            steps {
                sh 'docker run --rm -d -p 3000:3000 --name web-ctr webapp:${BUILD_NUMBER}'
            }
        }
    }
}
