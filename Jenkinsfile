
pipeline{
    tools{
       
        maven 'mymaven'
    }
	agent any
      stages{
           stage('Checkout the code'){
	    
               steps{
		 echo 'cloning the repo'
                 git 'https://github.com/Sonal0409/DevOpsClassCodes.git'
              }
          }
          stage('Compile'){
             
              steps{
                  echo 'complie the code again..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		  
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		  
              steps{
	         
                  sh 'mvn test'
              }
          
          }
        
          stage('Package'){
		  
              steps{
		  
                  sh 'mvn package'
              }
          }
	     
          stage('build Image'){
          
            steps{
                sh 'cp /var/lib/jenkins/workspace/CI-SCM-pipeline/target/addressbook.war .'
                sh 'docker build -t myaddressbook .'
            }
        }
	      stage('Deploy container'){
            steps{
                sh 'docker run -d -P yashsi08/myaddressbook'
            }
        }
      }
}
