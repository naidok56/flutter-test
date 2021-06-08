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
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {  
                sh 'echo "Hello World"'
             }
                
            }
        }
        stage('Distribute Android APK') {
              steps {
                  appCenter apiToken: '0f41449f9af45053cb183fd253ae2610a78a7c75',
                          ownerName: 'kylen.zn-gmail.com',
                          appName: 'Flutter-Demo-1',
                          pathToApp: 'build/app/outputs/apk/release/app-release.apk',
                          distributionGroups: 'Testers'
              }
        }
    }
}
