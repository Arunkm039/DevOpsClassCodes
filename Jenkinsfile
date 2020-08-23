#!usr/bin/env groovy
import hudson.model.*
import java.net.URL

node{
    stage('git checkout'){
        git 'https://github.com/Arunkm039/DevOpsClassCodes.git'
    }
    stage('compile'){
        withMaven(maven:'devops_maven'){
            sh 'mvn compile'
        }
    }
    stage('Test'){
        withMaven(maven:'devops_maven'){
            sh 'mvn test'
        }
    }
    stage('package'){
        withMaven(maven:'devops_maven'){
            sh 'mvn package'
        }
    }
    stage('DockerBuild'){
        sh 'cp /var/lib/jenkins/workspace/Package/target/addressbook.war .'
        sh 'sudo docker build . -t arunkm039/addbookapp:$BUILD_NUMBER'
        sh 'sudo docker push arunkm039/addbookapp:$BUILD_NUMBER'
        }
}
