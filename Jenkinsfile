node{
		
     stage('DATA ACQUISITION') {
	      
	      echo "DATA ACQUISITION"
	      
	      def task = "/var/lib/jenkins/workspace/ToolBox_Tasks/Freesurfer/Pending/Task.xml"
	      
	      if (fileExists (task)){
	      	echo task
	      }
	      else {
	      	echo "There're not taks pending"
	      }
	      	
     }
      
     stage('RECON-ALL TASK') {
	    
	    sshagent(['id_rsa_fsf']) {        
            sh 'ssh root@192.168.17.132'     
        }	
     }
      
     stage('DELIVERY RESULT') {
	      echo "DELIVERY RESULT"	
     }
      
     stage('NOTIFICATION') {
	 	 echo "NOTIFICATION"	   
     }
}
