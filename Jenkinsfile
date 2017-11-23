pipeline {
    agent {
        label 'slave'
    }

    stages {
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                    mkdir build
                    cd build
                    cmake ..
                    make -j
                '''
            }
        }
        stage('Run tests') {
            steps {
                sh '''#!/bin/bash
                    cd build
                    ctest
                '''
            }
        }
    }

    post {
        changed {
            sendNotifications currentBuild
        }
    }
}