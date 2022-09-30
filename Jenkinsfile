pipeline{
    agent any
    tools {
maven "Maven 3.8.6"
    }
    stages {
stage('1getcode'){
    steps{
        sh " echo ' cloning the latest app verion' "
       git "https://github.com/zamtechnologies/Mavenwebapp-"
    }
}
stage('2test+build'){
    steps{
        sh " echo 'running Junit test cases' "
        sh "mvn clean package"
    }
}
stage('3codequality'){
    steps{
    sh "mvn sonar:sonar"
    }
}
stage('4uploadartifacts'){
    steps{
        sh "mvn deploy"
    }
}
stage('5deploytoprod'){
    steps{ 
    deploy adapters: [tomcat9(credentialsId: 'tc cred', path: '', url: 'http://54.152.215.144:8080/')], contextPath: null, war: 'target/*war'
    }
}
}
}
