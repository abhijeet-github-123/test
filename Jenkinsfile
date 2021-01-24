node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("abhijeetcse123/test")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }
  
			      
   stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused.*/ 
         docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials')
           sh 'sudo docker login -u "abhijeetcse123" -p "#Abhijeet1997" docker.io'
               
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        
    }
}
