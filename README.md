# Student Hub

A lightweight student management app that runs in a browser. Add, search, edit, and remove student records; records are saved in that browser's local storage.

## Run locally

Open `manage.html` in a modern browser. No server, package installation, or database is required. The initial student list is sample data and is stored separately in each browser.

## Jenkins on GitHub push

1. Push this repository to GitHub and create a Jenkins **Pipeline** job.
2. In the job configuration, select **Pipeline script from SCM**, choose **Git**, enter this repository's URL and credentials if it is private, and set the script path to `Jenkinsfile`.
3. Ensure the Jenkins Git, Pipeline, and GitHub plugins are installed and that Jenkins is reachable by GitHub.
4. In GitHub, open **Settings → Webhooks → Add webhook**. Set the payload URL to `https://<your-jenkins-host>/github-webhook/`, content type to `application/json`, and choose **Just the push event**.
5. Save the webhook and run the Jenkins job once to verify checkout and build.

The pipeline checks out the latest revision on each GitHub push, verifies that `manage.html` is present, and archives it as a build artifact. If the repository is private or Jenkins requires a GitHub secret, configure credentials and webhook authentication in Jenkins/GitHub rather than committing them to this repository.
