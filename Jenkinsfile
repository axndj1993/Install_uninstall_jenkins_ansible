pipeline{
    agent any
	parameters{
		choice(name: 'task', choices: ['install','uninstall'], description: '')
	}
    stages{  
        stage("Execute Ansible"){
            steps{
				script {
                    if (params.task == 'install') {
                        echo "install jenkins"
						ansiblePlaybook credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'dev.inv', playbook: 'site.yml'
                    } else {
                        echo "un-install jenkins"
						ansiblePlaybook credentialsId: 'private-key', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'dev.inv', playbook: 'site_uninstall.yml'
                    }
                }
            }
        }
    }
}
