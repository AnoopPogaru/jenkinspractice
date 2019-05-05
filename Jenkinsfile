node('centos_mvn'){
    stage('cloning'){
        git branch: 'dev', url: 'https://github.com/bhaskardegala/jenkinspractice.git'
    }
    stage('clean'){
        sh 'mvn clean'
    }
    stage('package'){
        sh 'mvn package'
    }
    stage('pwd'){
        sh 'pwd'
    }
    stage('archive'){
        archiveArtifacts '/pipescm/target/*.jar'
    }
    stage('test reports'){
        junit '/pipescm/target/surefire-reports/*.xml'
    }
}
