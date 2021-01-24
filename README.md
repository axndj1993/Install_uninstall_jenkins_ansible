# Jenkins job to install/un-install jenkins on an EC2 instance using Ansible

```
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
```

Watch this youtube video as a referene to create credentials and also how to use pipeline syntax
https://www.youtube.com/watch?v=PRpEbFZi7nI
