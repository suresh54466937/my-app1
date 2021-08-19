node{
    stage('SCM checkout'){
        https://github.com/Ram9500/my-app1.git
    stage('compile package'){
        def mvnHome = tool name: 'maven-3', type: 'maven'
        sh "${mvnHome}/bin/mvn package"
    }
  }
}
