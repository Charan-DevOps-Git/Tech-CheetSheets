# Jenkins Commands

## Managing Jobs

- jenkins-jobs list: List all Jenkins jobs.
- jenkins-jobs update [job_name]: Update a Jenkins job from a YAML file.
- jenkins-jobs delete [job_name]: Delete a Jenkins job.

## Using the Jenkins CLI

- java -jar jenkins-cli.jar -s http://[jenkins_url] list-jobs: List all Jenkins jobs.
- java -jar jenkins-cli.jar -s http://[jenkins_url] build [job_name]: Trigger a build for a specific job.
- java -jar jenkins-cli.jar -s http://[jenkins_url] get-job [job_name]: Retrieve the job configuration.
- java -jar jenkins-cli.jar -s http://[jenkins_url] create-job [job_name] < [config.xml]: Create a new job from an XML configuration file.
- java -jar jenkins-cli.jar -s http://[jenkins_url] delete-job [job_name]: Delete a job.

## Managing Plugins

- java -jar jenkins-cli.jar -s http://[jenkins_url] install-plugin [plugin_name]: Install a Jenkins plugin.
- java -jar jenkins-cli.jar -s http://[jenkins_url] list-plugins: List installed plugins.
- java -jar jenkins-cli.jar -s http://[jenkins_url] uninstall-plugin [plugin_name]: Uninstall a Jenkins plugin.
- java -jar jenkins-cli.jar -s http://[jenkins_url] restart: Restart Jenkins.
