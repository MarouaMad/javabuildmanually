node {
   
   stage('git clone') {
   git branch: 'main', credentialsId: 'gitlab', url: 'git@gitlab.com:formation_09_2022/projet1_j2e.git'
}

   stage('Build') {
    sh 'mvn clean install package'
}

   stage('deploy') {
       deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://13.38.130.95:8080/')], contextPath: null, war: '**/*.war'
   }
   
   
  
   
}
