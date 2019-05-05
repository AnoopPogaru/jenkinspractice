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
        archiveArtifacts '/springpetclinic/target/*.jar'
    }
    stage('test reports'){
        junit '/springpetclinic/target/surefire-reports/*.xml'
    }
}
