node{
		
     stage('DATA ACQUISITION') {
	      
	      echo "DATA ACQUISITION"
	      
	      def task = new File ("/var/lib/jenkins/workspace/ToolBox_Tasks/Freesurfer/Pending/Task.xml")
	      def pomFile = new XmlSlurper().parse(file)
	      def pomModules = pomFile.modules.children().join(",")
    	  	      
	      if (fileExists (task)){
	      	echo task
	      }
	      else {
	      	error("${task} still missing. Will now fail the job.")
	      }
	      	
     }
      
     stage('DATA PROCESSING-recon-all') {
	    
	    echo "Connecting to Freesuefer server"
	    
	    sshagent(['id_rsa_fsf']) {        
	    
            sh 'ssh root@192.168.17.132'     
            
        }
                	
     }
      
     stage('DATA STORAGED') {
	      echo "DELIVERY RESULT"	
     }
      
     stage('NOTIFICATION') {
	 	 echo "NOTIFICATION"	   
     }
}
