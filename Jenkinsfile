node {
    
  stage('git clone') {
      
    git branch: 'main', credentialsId: 'gitlab', url: 'git@gitlab.com:formation_09_2022/projet1_j2e.git'
}
     
  stage('build'){
    sh 'mvn clean install package'
  }
  stage("deploy"){
      
    deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://13.36.195.131:8080')], contextPath: null, war: '**/*.war'
}
}
