pipeline  {
  agent {
    docker {
      image 'maven:3-alpjine'
      args '-v root/.m2:/root/.m2'
    }
  }
  stages {
    stage ('build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
  }
}
