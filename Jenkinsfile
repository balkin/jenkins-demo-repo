// Every jenkins file should start with either a Declarative or Scripted Pipeline entry point.
node {
    //Utilizing a try block so as to make the code cleaner and send slack notification in case of any error
    try {
        // Stage, is to tell the Jenkins that this is the new process/step that needs to be executed
        stage('Checkout') {
            // Pull the code from the repo
            checkout scm
        }

        stage('Build Image') {
            // Build our docker Image
            sh("echo docker build -t tagname:latest .")
        }

        stage('Run application test') {
            // If you need environmental variables in your image. Why not load it attach it to the image, and delete it afterward
            sh("echo docker run --env-file .env --rm tagname:latest gradlew test")
        }

        stage('Deploy application') {
            // This is the cool part where you deploy. Here, you can specify builds you want to deploy
            switch (env.BRANCH_NAME) {
                case "master":
                    sh("echo deploy to prod")
                    break
                case "dev":
                    sh("echo deploy to stg")
                    break
            }
        }
    } catch (e) {
        currentBuild.result = "FAILED"
        throw e
    } finally {
        echo "Notify"
    }
}

/*
node {
	stage 'Checkout'
		checkout scm

	stage 'Build'
		bat 'nuget restore SolutionName.sln'
		bat "\"${tool 'MSBuild'}\" SolutionName.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"

	stage 'Archive'
		archive 'ProjectName/bin/Release/**'

}
 */
