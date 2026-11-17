# Student Hub — Project Write-up

## What we built

Student Hub is a simple student management application in `manage.html`. It shows sample student records and lets a user add, search, edit, and delete records. Data is saved in the browser's local storage, so this simple version does not use a server or shared database.

We also added a `Jenkinsfile`. It tells Jenkins to fetch the repository, check that the app file exists, and save it as a build artifact.

## Run the application

Open `manage.html` in a modern web browser. No installation is needed.

## Small JavaScript example

This two-line example creates a student list and adds one student:

```javascript
const students = [];
students.push({ name: "Ava", course: "Computer Science" });
```

## GitHub and Jenkins setup

1. Push the project to the GitHub repository. From the project folder, run `git push -u origin main` and sign in to GitHub if asked.
2. Install Jenkins with the **Git**, **Pipeline**, and **GitHub** plugins.
3. Create a Jenkins **Pipeline** job. Choose **Pipeline script from SCM**, select **Git**, enter the repository URL, set the branch to `main`, and set the script path to `Jenkinsfile`.
4. Make sure Jenkins has a public HTTPS address that GitHub can reach. A local address such as `http://localhost:8080` is not reachable by GitHub.
5. In GitHub, go to **Settings → Webhooks → Add webhook**. Set the payload URL to your Jenkins address plus `/github-webhook/`, choose `application/json`, and select **Just the push event**.
6. Save the webhook and run the Jenkins job to test it. After setup, GitHub pushes should trigger Jenkins to fetch and build the project.

The GitHub webhook and Jenkins job must be configured using your own Jenkins server. The project commits are local until they are successfully pushed to GitHub; keep passwords and tokens out of project files.
