pipeline {
    agent any

    stages {
        stage('GIT PULL') {
            steps {
                git branch: "main", url: 'https://github.com/naidok56/flutter-test.git'
            }
        }
        stage ('Flutter Doctor') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {
                sh "flutter doctor -v"
                }
            }
        }
        stage('BUILD') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {  
                sh 'flutter build apk'
             }
                
            }
        }
        stage('Distribute Android APK') {
              steps {
                  appCenter apiToken: '03cebc8efabbcc1d36ee91cd71b249ea6eadc102',
                          ownerName: 'kylen.zn-gmail.com',
                          appName: 'Flutter-Demo-1',
                          pathToApp: 'build/app/outputs/flutter-apk/app-release.apk',
                          distributionGroups: 'Testers'
              }
        }
        stage('Flutter Build iOS') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {
                sh "flutter build ios --release --no-codesign"
                }
            }
        }
        stage('Make iOS IPA And Distribute') {
                steps {
                    dir('ios'){
                            sh "bundle install"
                            sh "bundle exec fastlane buildAdHoc --verbose" 
                    }
                }
        }
        stage('Cleanup') {
            steps {
                withEnv(['PATH+EXTRA=/usr/sbin:/usr/bin:/sbin:/bin']) {
                sh "flutter clean"
                }
            }
        }
    }
}
