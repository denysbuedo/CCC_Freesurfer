node{
		
     stage('DATA ACQUISITION') {
		
		//Read new task data
		echo "Reading the task data"
		def tast_xml = readFile "/var/lib/jenkins/workspace/ToolBox_Tasks/Freesurfer/Pending/Task2.xml"
		def parser = new XmlParser().parseText(tast_xml)
		def JOB_NAME = "${parser.attribute("job_name")}"
		def BUILD_ID ="${parser.attribute("build")}"
		def OWNER ="${parser.attribute("owner_task")}"
		def SUBJECT="${parser.attribute("subject")}"
		def FSF_SUBJECT="${parser.attribute("fsf_output")}"
		
		//Setting Build
		currentBuild.displayName = "BUILD# $BUILD_ID- $OWNER"  
		
		//Copy de Subject file to SUBJECT_DIR in Freesuerfer Server
		echo "Connecting to freesurfer server to copy subject file"
		sshagent(['id_rsa_fsf']) {      
			def subject_data = new File ("$JENKINS_HOME/workspace/$JOB_NAME/subject_file")  
			sh "scp $subject_data root@192.168.17.132:/usr/local/freesurfer/subjects/"
        }
     }
      
     stage('DATA PROCESSING recon-all') {
	    
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
