pipeline {

  agent any

  options { 
  
   buildDiscarder(logRotator(numtoKeepStr: '2', artifactNumtoKeepStr: '1'))

  }

  stages {
     stage {'Unit Tests') {
       steps {
         sh 'ant -f test.xml -v'
         junit 'reports/result.xml'
        }

      }
     stage('build') {
     steps {
       sh 'ant -f build.xml -v'
     }

    }

 }


 post {
   always {
     archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
   }
 }

}
