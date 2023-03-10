pipeline{
  agent any
  stages{
  stage('Clean') {
    steps{
      bat "mvn clean"
    }
    }
    stage('Test') {
       steps{
      bat "mvn test"
    }
    }
    stage('Package') {
        steps{
      bat "mvn package"
    }
    }
    stage('Deploy') {
            steps{
         deploy adapters: [tomcat9(credentialsId: '17ad82d6-48c2-40e8-87e4-7649da3d0496', path: '', url: 'http://localhost:9090')], contextPath: null, war: 'target/*.war'
        }
        }
    stage("Consolidated Result"){
      steps{
        input("Do you want to test result?")
        junit'**/target/surefire-reports/Test-*.xml'
        archive 'target/*.jar'
      }
    }

  }
}