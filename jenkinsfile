pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'e7112adb-17ba-470c-afc6-3b10b31f3d5c', url: 'git@github.com:hongwenYang/jenkinsdemo.git']]])
            }
        }
        stage('build project') {
            steps {
                sh '''#!/bin/bash -il
mvn clean package'''
            }
        }
        stage('publish') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '119c18eb-fedb-44e7-b4d6-911f29cde5b2', path: '', url: 'http://106.52.88.248:8083')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}
