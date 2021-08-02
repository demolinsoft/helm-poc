def repo="https://github.com/demolinsoft/helm-poc.git"
pipeline{
		agent{
			label 'helm'
		}
		stages{
				
                stage("add Repo") {
                        steps {
                               sh "helm repo add shailendra ${repo}"
                            }
                    }
				stage("Deploy to Dev") {
                        steps {
                            script{
					openshift.withCluster(){
                                        sh "helm upgrade --install helm-app shailendra/sample-app --values dev/values.yaml -n dev --wait"
                                    }
                                }
                            }
                    }
                stage("Deploy to UAT") {
                        steps {
                            script{
					openshift.withCluster(){
                                        sh "helm upgrade --install helm-app shailendra/sample-app --values uat/values.yaml -n uat --wait"
                                    }
                                }
                            }
                    }
            }
        }
