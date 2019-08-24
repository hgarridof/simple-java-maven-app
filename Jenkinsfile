pipeline  {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }
  }
  stages {
    stage ('build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage ('tests') {
      steps {
        sh 'mvn test'
      }
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }
      }
    }
    stage ('deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }
  }
}
