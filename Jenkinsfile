pipeline {
agent any
    stages {
        stage('SCM') {
            steps {
                // Get some code from a GitHub repository
                   git credentialsId: 'github_credential', url: 'https://github.com/jincyjijo/spring3-mvc-maven-xml-hello-world.git'
                              
            }
        }  
   stage('Build') {
            steps {
                // maven packages
                     sh "mvn -Dmaven.test.failure.ignore=true clean package"
                              
            }

            
       }
   
   stage ('Artifacts') {
            steps {
                
                 archiveArtifacts 'target/*.war'
                }
           }
         
        stage('deploy') {
            steps {
                // Tomcat deploy
                    
                    sh "curl -v -u admin:adminadmin -T /var/lib/jenkins/workspace/spring3/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://ec2-44-211-60-58.compute-1.amazonaws.com:8080/manager/text/deploy?path=/jithin&update=true'"
                              
               }    
           
            
           } 
   
  
            
    }
        
    }
