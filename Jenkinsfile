node('centos_mvn'){
    stage('cloning'){
        git branch: 'dev', url: '$file_location'
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
        archiveArtifacts 'target/*.jar'
    }
    stage('test reports'){
        junit 'target/surefire-reports/*.xml'
    }
    stage('creating specified build no folder'){
        sh 'cd ~'
        sh 'mkdir build${BUILD_ID}'
        sh 'pwd'
    }
    stage('moving artifacts'){
        sh 'cd ~'
        sh 'cp  workspace/test.first/target/*.jar build${BUILD_ID} '
    }
}
