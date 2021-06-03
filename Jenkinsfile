pipeline {
    agent any

    stages {
        stage('GIT PULL') {
            steps {
                git branch: "main", url: 'https://github.com/naidok56/flutter-test.git'
            }
        }
        stage('BUILD') {
            steps {
                sh "flutter build apk --debug"
            }
        }
    }
}
