node{
		
     stage('DATA ACQUISITION') {
	      echo "DATA ACQUISITION"	
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
