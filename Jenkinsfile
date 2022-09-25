node {
    
    stage('git clone') {
        
   git branch: 'main', credentialsId: 'gitlab', url: 'git@gitlab.com:formation_09_2022/projet1_j2e.git'
   
   }
   
   stage('SonarQube analysis') {
    withSonarQubeEnv {
     sh 'mvn clean package sonar:sonar'
    }
 }
   
   stage('Quality Gate') {
     waitForQualityGate abortPipeline: true

   }
   
   
   stage('build') {
    sh 'mvn clean install package' 
    
   } 

    stage('Deploy') {
    deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://172.31.37.227:8080')], contextPath: null, war: '**/*.war'
}
  
    
    
}
