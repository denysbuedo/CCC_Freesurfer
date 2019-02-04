node{
		
     //Read new task data
	 echo "Reading the task data"
     def tast_xml = readFile "/var/lib/jenkins/workspace/ToolBox_Tasks/Freesurfer/Task.xml"
	 def parser = new XmlParser().parseText(tast_xml)
	 def JOB_NAME = "${parser.attribute("job_name")}"
	 def BUILD_ID ="${parser.attribute("build")}"
	 def OWNER ="${parser.attribute("owner_task")}"
	 def SUBJECT="${parser.attribute("subject")}"
	 def FSF_SUBJECT="${parser.attribute("fsf_output")}"
	 
	 //Setting Build description
	 currentBuild.displayName = "BUILD# $BUILD_ID- $OWNER"  
	
	 //Copy data from Jenkins Server to FreeSurfer Subject directory.
     stage('DATA ACQUISITION') {
		
		//Copy de Subject file to SUBJECT_DIR in Freesuerfer Server
		echo "Connecting to freesurfer server to copy subject file"
		sshagent(['id_rsa_fsf']) {      
			//Create de subject file
			def subject = new File ("$JENKINS_HOME/workspace/$JOB_NAME/$SUBJECT")
			echo "Deleting task file from Jenkins Server"
			sh "rm -f $JENKINS_HOME/workspace/$JOB_NAME/$SUBJECT"
			sh "scp $subject root@192.168.17.132:/usr/local/freesurfer/subjects/"
        }
     }
      
     stage('DATA PROCESSING') {
     
	    echo "Connecting to Freesuefer server and execute recon-all task"
	    sshagent(['id_rsa_fsf']) {  
			sh "ssh root@192.168.17.132 /usr/local/freesurfer/subjects/RunFreeSurfer_eApp.sh $SUBJECT $FSF_SUBJECT"
        }
     }
      
     stage('DATA STORAGED') {
	      echo "DELIVERY RESULT"	
     }
      
     stage('NOTIFICATION') {
	 	 echo "NOTIFICATION"	   
     }
}
