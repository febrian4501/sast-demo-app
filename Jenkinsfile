pipeline {
 agent any

  stages {
    stage('Checkout') {
      steps {
       git url: 'https://github.com/febrian4501/sast-demo-app.git', branch:'main'
     }
   }
   stage('SAST Analysis') {
     steps {
       sh 'bandit -f xml -o bandit-output.xml -r . || true'
       recordIssues tools: [bandit(pattern: 'bandit-output.xml')]
     }
   }
 }
}
