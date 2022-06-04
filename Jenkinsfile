node {
    
    stage('Clone') {
        
        git credentialsId: 'jenkins', url: 'git@gitlab.com:iset-kairouan/projet_j2ee.git'
    
    }
    
    stage('Build') {
        
        withMaven(maven: 'Maven') {
            sh 'mvn clean install package'
            }
        }
        
    stage('Deploy-tomcat') {
        
        deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://13.36.103.14:8080/')], contextPath: null, war: '**/*.war'
    }
}
