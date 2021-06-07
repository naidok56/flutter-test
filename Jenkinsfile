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
                sh "flutter build apk"
            }
        }
        stage('Distribute Android APK') {
              steps {
                  appCenter apiToken: '0f41449f9af45053cb183fd253ae2610a78a7c75',
                          ownerName: 'Kylen Naidoo',
                          appName: 'Flutter-Demo',
                          pathToApp: 'build/app/outputs/apk/release/app-release.apk',
                          distributionGroups: 'Testers'
              }
        }
    }
}
