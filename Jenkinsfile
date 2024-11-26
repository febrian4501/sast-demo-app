pipeline {
 agent any

  stages {
    stage('Checkout') {
      steps {
       git url: 'https://github.com/febrian4501/sast-demo-app.git', branch:'main'
            }
   }
   stage('Install Dependencies') {
     steps {
       sh 'sudo apt install python3-bandit'
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
