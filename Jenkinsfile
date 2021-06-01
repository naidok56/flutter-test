pipeline {
    agent any

    stages {
        stage('GIT PULL') {
            steps {
                git branch: "main", credentialsId: 'naidok56', url: 'https://github.com/naidok56/flutter_ocr.git'
            }
        }
        stage('TEST') {
            steps {
                sh 'flutter test'
            }
        }
        stage('BUILD') {
            steps {
                sh '''
                  #!/bin/sh
                  flutter build apk --debug
                  '''
            }
        }
    }
}
