pipeline{
	agent any 
	stages{
		stage('parallel-job1'){
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
				sh 'sudo find / -name jenkins'
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
				sh 'id ubuntu'	
			}
		}
		stage('parallel-job2'){
			parallel{
				stage('sub-job3'){
					steps{
                        sh 'sort -r /etc/passwd'
                        sh 'bash /var/lib/jenkins/workspace/parallel-job1/security.sh'
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
