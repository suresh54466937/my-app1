node{
   stage('SCM Checkout'){
     git https://github.com/Ram9500/my-app1.git
   }
   stage('Compile-Package'){

      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn clean package"
	  sh 'mv target/myweb*.war target/newapp.war'
   }
}
