Below are steps followed to create a partent project as jar and then copy the jar dependency in the child maven project


Step 1: Create a Java Maven Project in Eclipse
Open Eclipse and go to File -> New -> Project.
Choose Maven -> Maven Project and click Next.
Check the option Create a simple project (skip archetype selection) and click Next.
Enter the Group Id and Artifact Id for your project. Click Finish.
Step 2: Add Code to the Maven Project
Add your Java code or resources to the src/main/java or src/main/resources folders.

Step 3: Configure the POM.xml file
Open the pom.xml file in your Maven project. Add the necessary dependencies and configurations.

Step 4: Push the Project to GitHub
Initialize a Git repository if not already done:
bash
Copy code
git init
Add a remote repository (replace your-username and your-repository with your GitHub username and repository name):
bash
Copy code
git remote add origin https://github.com/your-username/your-repository.git
Commit and push your project to GitHub:
bash
Copy code
git add .
git commit -m "Initial commit"
git push -u origin master
Step 5: Use the Project as a POM Dependency in Another Project
Now, in your other Maven project (the one where you want to use the first project as a dependency):

Open the pom.xml file.

Add the dependency for the first project:

xml
Copy code
<dependencies>
    <dependency>
        <groupId>com.example</groupId>
        <artifactId>your-maven-project</artifactId>
        <version>1.0.0</version>
    </dependency>
</dependencies>
Replace com.example, your-maven-project, and 1.0.0 with the appropriate values for the first Maven project.

Step 6: Install the First Project Locally (if not on a public repository)
If your first Maven project is not on a public repository, you need to install it locally before it can be used as a dependency:

bash
Copy code
mvn install
Step 7: Update Maven Project
Right-click on your second project in Eclipse, then choose Maven -> Update Project. This will fetch the first project as a dependency and update your second project.

Now, your second project should be able to use classes/resources from the first project as if they were part of it. Ensure that your first project is successfully built and available in the local Maven repository or a public repository accessible to your second project.

You can add the token to your settings.xml file (usually located in the .m2 directory) or directly in the pom.xml file (not recommended for security reasons).
Here's an example of how to include the token in the settings.xml file:

<servers>
    <server>
        <id>github</id>
        <username>YOUR_GITHUB_USERNAME</username>
        <password>YOUR_PERSONAL_ACCESS_TOKEN</password>
    </server>
</servers>
