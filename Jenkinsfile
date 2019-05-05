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
    stage('archive'){
        archiveArtifacts '/target/*.jar'
    }
    stage('test reports'){
        junit '/target/surefire-reports/*.xml'
    }
}
