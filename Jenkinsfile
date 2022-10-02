pipeline{
	agent any 
	stages{
		stage('parallel-job'){
			parallel{
				stage('sub-job1'){
					steps{
						echo 'action1'
						sh 'pwd'
					}
				}
				stage('sub-job2'){
					steps{
						echo 'action2'
						sh 'lscpu'
						sh 'lsblk'
						sh 'cat /etc/passwd'
					}
				}
			}
		}
		stage('1-git-clone'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github-id', url: 'https://github.com/akudogithub/jenkins-parallel.git']]])
			}
		}
		stage('2-maven-build'){
			steps{
				sh 'find / -name jenkins'
				sh 'id jenkins'
			}
		}
		stage('3-code-analysis'){
			steps{
				sh 'date'
				sh 'cal'
			}
		}
		stage('4-code-deploy'){
			steps{
				sh '$(SHELL)'
				sh '$(LOGNAME)'	
			}
		}
		stage('parallel-job'){
			parallel{
				stage('sub-job3'){
					steps{
                        sh 'sort -r /etc/passwd'
					}
				}
				stage('sub-job4'){
					steps{
						sh 'more /etc/passwd'
						sh 'sort /etc/passwd'
					}
				}
			}
		}
	}
}
