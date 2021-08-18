pipeline {
    agent any 
    stages {
	stage('Maven Compile'){
		steps{
			echo 'Project compile stage'
			bat label: 'Compilation running', script: '''mvn compile'''
	       	}
	}
	
	stage('Unit Test') {
	   steps {
			echo 'Project Testing stage'
			bat label: 'Test running', script: '''mvn test'''
	       
       		}
   	}

	stage('Jacoco Coverage Report') {
        	steps{
            		jacoco()
		}
	}
        
	stage('Jmeter Tests'){
		steps{
			echo 'Project performance testing stage'
			bat label: 'Project packaging', script: '''jmeter -jjmeter.save.saveservice.output_format=xml 
  						-n -t src/main/resources/customerDemoFinal.jmx -l src/main/resources/report2.jtl'''
		}
	} 	
	    
	stage('Maven Package'){
		steps{
			echo 'Project packaging stage'
			bat label: 'Project packaging', script: '''mvn package'''
		}
	} 	
    }
}

