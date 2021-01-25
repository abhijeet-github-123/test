pipeline { 



    environment { 



        registry = "abhijeetcse123/test" 



        registryCredential = 'dockerhub_id' 



        dockerImage = '' 



    }



    agent any 



    stages { 



        stage('Cloning our Git') { 



            steps { 



                git 'https://github.com/abhijeet-github-123/test.git'



            }


        } 



        stage('Building our image') { 



            steps { 



                script { 



                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 

                }



            } 



        }



        stage('Deploy our image') { 



            steps { 



                script { 



                    docker.withRegistry( '', registryCredential ) { 



                        dockerImage.push() 



                    }



                } 


            }



        } 


            }

        } 


 


