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
        sh 'mkdir /home/jenkins/build${BUILD_ID}'
    }
    stage('moving artifacts'){
        sh 'cp  target/*.jar /home/jenkins/build${BUILD_ID}'
        sh 'echo ${BUILD_ID}'
    }
    stage('SonarQube analysis'){
    // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
    withSonarQubeEnv('SONAR-6.7.4'){
      // requires SonarQube Scanner for Maven 3.2+
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
    }
    }
