pipeline{
	agent any
	// tools{
	// 	maven "test-maven"
	// }
      stages{
           stage('Checkout'){
	    
               steps{
		 echo 'cloning..'
                 git 'https://github.com/akshu20791/DevOpsClassCodes.git'
              }
          }
          stage('Compile'){
             
              steps{
                  echo 'compiling..'
                  bat 'mvn compile'
	      }
          }
          stage('CodeReview'){
		  
              steps{
		    
		  echo 'codeReview'
                  bat 'mvn pmd:pmd'
		  recordIssues(tools: [pmdParser()])
              }
          }
           stage('UnitTest'){
		  
              steps{
	         
                  bat 'mvn test'
              }
               post {
               success {
                   junit 'target/surefire-reports/*.xml'
               }
           }	
          }
          
          stage('Package'){
		  
              steps{
		  
                  bat 'mvn package'
              }
          }
	     
          
      }
}
