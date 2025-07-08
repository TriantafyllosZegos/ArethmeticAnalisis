---
 
# Overview
 
This project focuses on implementing Salesforce solutions for an energy provider company using SFdy, an SFDX alternative. The goal is to streamline customer management, improve service efficiency, and enhance data analytics capabilities.

---
# Introduction
 
This wiki provides detailed documentation for the Salesforce project aimed at enhancing the operational efficiency of an energy provider company using SFdy. It covers project objectives, setup instructions, development guidelines, deployment processes, and best practices.

---
# Prerequisites
- [Node.js](#https://nodejs.org/en/download) (latest version)
- [Visual Studio Code](#https://code.visualstudio.com/download)
 
---
# Table of Contents
[[_TOC_]]

---
# Getting Started 

## Cloning the Repository

1. Open your terminal or command prompt.
2. Navigate to the directory where you want to clone the repository.
3. Use the following command to clone the repository:

```bash
# HTTPS
git clone https://dkakales@dev.azure.com/dkakales/Energy_POC/_git/Energy_POC

# SSH
git clone git@ssh.dev.azure.com:v3/dkakales/Energy_POC/Energy_POC
```
---
## Installing SFDY
1. Open your terminal or command prompt and type the following command

```bash
npm install -g sfdy
```

## Initializing SFDY
1. Open a terminal or command prompt in your project folder.
2. Use the following command to initialize sfdy in your project.

```bash
sfdy init
```

For more information regarding sfdy : https://github.com/micheletriaca/sfdy

---
## Installing fast-sfdc extension in Visual Studio
In Visual Studio install the extension shown below: 

![image.png](/.attachments/image-304fec24-71c0-4651-b28a-0727dca38d57.png)

OR 

use the extension id to find it: 
     `m1ck83.fast-sfdc`

---
## Authorize an org
Using the `fast-sfdc` extension we will authorize our org.

1. Type the command below in Visual Studio Code <br>
![image.png](/.attachments/image-147690c5-2b08-4bb9-a7b9-ebaa29026125.png)

2. A new message will appear in the bottom left side of Visual Studio Code saying `fast-sfdc not logged in`.<br>
![image.png](/.attachments/image-ac9cb843-a401-4684-b2f5-82ae582e7409.png)
<br>
3. You click on this message and the following commands appear:<br> 
![image.png](/.attachments/image-bb52149a-2ba8-48d4-b5b9-1682bc57bd1b.png)

    Where you choose the following options:
   - [Add credential]
   - [Username + password and token]
   - [Production/Developer]
   - Type in the username
   - Type in your password+token 
   - Type in any name 
   - Compile on save (false recommended but optional)
   - Add .gitignore NO
<br>

4. Your explorer should now have these files:

   ![image.png](/.attachments/image-1c24c519-3af4-4edb-9c74-3357186343a6.png)

---
## Retrieving metadata
In the Visual Studio when you click in the cloud option of the left side menu. All the available metadata will appear. 
>If nothing appears, disable all filters.

  ![image.png](/.attachments/image-b894fe40-2948-490f-b145-66f0d42ccfe3.png)

You can retrieve any metadata by clicking on the cloud icon in the right side of the name of the folder or file.

---
## ESLint and PMD Setup

This guide will help you set up ESLint and PMD on your local machine to maintain code quality and consistency. Follow the steps below after cloning the project from the `devshared` branch, which contains all necessary configuration files.

### ESLint Setup

1. **Initialize npm:**
   Open your terminal and navigate to the root directory of the cloned project. Run the following command to initialize npm:
   ```bash
   npm init -y
   ```

2. **Install ESLint:**
   Install ESLint version 7.32.0 by running:
   ```bash
   npm install eslint@7.32.0
   ```

3. **Set Up ESLint Configuration:**
   The `devshared` branch provides a pre-configured `.eslintrc` file. Ensure this file is in the root directory of your project.

4. **Install ESLint Extension for VSCode:**
   Ensure you have the ESLint extension installed in Visual Studio Code. You can install it from the Extensions view (`Ctrl+Shift+X`) by searching for `ESLint`.

### PMD Setup

1. **Install PMD Extension for VSCode:**
   Install the PMD extension from the Extensions view (`Ctrl+Shift+X`) by searching for `PMD`. This extension will help you integrate PMD with your development environment.

2. **Add PMD Ruleset:**
   The `devshared` branch provides a `pmd-ruleset.xml` file. After installing the PMD extension, you need to add this file to the optional rules of the PMD extension:
   - Go to the PMD extension settings in VSCode.
   - Locate the option to add an optional ruleset.
   - Add the path to the `pmd-ruleset.xml` file located in the root directory of the cloned project.  
   
 ![image.png](/.attachments/image-0d9f7123-b1e6-451d-b130-dd65f5243c19.png)


### Provided Files

The following files are provided in the `devshared` branch and should be in the root directory of your cloned project:
- `package.json`
- `.eslintrc`
- `pmd-ruleset.xml`

In case you get errors after following these steps try replacing your local files with those provided from the remote branch.

### Summary

By following these steps, you will set up ESLint and PMD in your development environment, ensuring that your code adheres to the project's quality standards. If you encounter any issues or have questions, feel free to reach out to the project maintainers.

Happy coding!

---
# Developer Guidelines

---
## Branch Release Strategy
![devopsDiagram.drawio.png](/.attachments/devopsDiagram.drawio-7b5e2166-db30-4078-ae86-dc11b9d5a32f.png)

---
## Conflict Resolution Strategy

Conflict resolution using a temporary branch in Visual Studio Code (VS Code) is a common approach to ensuring a smooth workflow, especially when working with a team and adhering to a pull request-based process for committing to the devshared branch. Below are the steps to resolve conflicts using a temporary branch through VS Code:

### Steps to Resolve Conflicts with a Temporary Branch in VS Code

#### 1. Ensure Prerequisites
- **Git**: Ensure Git is installed on your machine.
- **VS Code**: Install Visual Studio Code.
- **Extensions**: Install the necessary VS Code extensions, such as "GitLens" for enhanced Git capabilities.

#### 2. Create a Temporary Branch
- Open VS Code and open your project folder.
- Open the terminal in VS Code (``Ctrl+` ``).
- Create a new branch from the devshared branch:

    ```sh
    git checkout devshared
    ```
    ```sh
    git pull origin devshared
    ```
    ```sh
    git checkout -b temp-branch
    ```

#### 3. Identify and Resolve Conflicts
- **Merge Changes** from the branch with conflicts (e.g., `feature-branch-with-conflicts`) into the temporary branch:
    ```sh
    git merge feature-branch-with-conflicts
    ```
- VS Code will automatically detect conflicts. You can see the conflicts in the **Source Control** panel or directly in the editor.

- **Resolve Conflicts**:
    - VS Code provides inline conflict resolution. You will see markers like `<<<<< HEAD`, `=======`, and `>>>>> feature-branch`.
    - Choose which changes to keep or manually edit the file to resolve the conflicts.
    - After resolving, remove the conflict markers and save the files.

- **Mark the conflicts as resolved** and commit the changes:
    ```sh
    git add .
    ```
    ```sh
    git commit -m "Resolved merge conflicts between devshared and feature-branch-with-conflicts"
    ```

#### 4. Push the Temporary Branch
- Push the temporary branch to the remote repository:
    ```sh
    git push origin temp-branch
    ```

#### 5. Create a Pull Request
- Go to your repository on Azure.
- Create a pull request to merge `temp-branch` into `devshared`.
- In the pull request description, explain the conflict resolution process and changes made.

#### 6. Review and Merge the Pull Request
- Request a review from your team members.
- Once approved, merge the pull request into the `devshared` branch.
- Delete the local temporary branch and both local and remote new feature branches after merging to keep the repository clean:

    ```sh
    git branch -d temp-branch
    ```
    ```sh
    git branch -d feature-branch-with-conflicts
    ```
    ```sh
    git push origin --delete feature-branch-with-conflicts
    ```

### Example Scenario in VS Code
1. **Opening the Project**: Open the project in VS Code.
2. **Creating a Temporary Branch**:
    - Open the terminal in VS Code.
    - Run the commands to create and switch to a new temporary branch.
3. **Merging and Resolving Conflicts**:
    - Use the VS Code interface to merge the `feature-branch-with-conflicts` into `temp-branch`.
    - VS Code highlights conflicts in the editor.
    - Use the conflict resolution options (e.g., `Accept Current Change`, `Accept Incoming Change`, `Accept Both Changes`) provided by VS Code to resolve conflicts.
4. **Committing and Pushing Changes**:
    - Once conflicts are resolved, stage the changes.
    - Commit with a meaningful message.
    - Push the temporary branch to the remote repository.
5. **Creating and Merging the Pull Request**:
    - Navigate to your repository on Azure.
    - Create a pull request from `temp-branch` to `devshared`.
    - After review and approval, merge the pull request.
----

## **Working with Boards in Azure DevOps**

### Introduction

Azure DevOps Boards provide a rich set of features for planning and tracking work, including support for Kanban boards, backlogs, team dashboards, and custom reporting. This guide will focus on managing user stories and ensuring a smooth workflow from backlog to completion.

### Workflow Overview

In our project, we have the following boards to manage the status of our work items:

1. **Backlog**
2. **In Analysis**
3. **Develop**
4. **Testing**
5. **Release**
6. **Done**

### Creating and Processing User Stories

#### 1. **Adding a User Story to the Backlog**

When a new user story is created, it is initially added to the **Backlog**. 

- **Status**: "To be processed" (Custom field)
- **Action Required**: The user story is reviewed and prioritized by the product owner or a team member responsible for backlog grooming.

#### 2. **Moving User Story to Analysis**

Once a user story is ready to be detailed and analyzed:

- **Board**: Move the user story from **Backlog** to **In Analysis**.
- **Action Required**: A team member is assigned to analyze the user story. This includes refining the requirements, adding acceptance criteria, and estimating effort.

#### 3. **Development Phase**

After the analysis is complete:

- **Board**: Move the user story from **In Analysis** to **Develop**.
- **Action Required**: Assign the user story to a developer who will implement the necessary code changes. The status should be updated to reflect that development work has started.

#### 4. **Testing Phase**

Once the development is complete and code changes are merged:

- **Board**: Move the user story from **Develop** to **Testing**.
- **Action Required**: Assign the user story to a QA tester who will perform the necessary tests to ensure the functionality works as expected.

#### 5. **Release Preparation**

After successful testing:

- **Board**: Move the user story from **Testing** to **Release**.
- **Action Required**: Prepare the user story for deployment. This might involve code reviews, preparing release notes, or coordinating with other teams.

Only the release manager can move a User story on the release stage
#### 6. **Completing the User Story**

When the user story has been released to production and all tasks are complete:

- **Board**: Move the user story from **Release** to **Done**.
- **Status**: Update the status to "Done".
- **Action Required**: Ensure all documentation is updated, and any relevant stakeholders are informed of the release.

### **Best Practices**

- **Regular Grooming**: Regularly review and prioritize the backlog to ensure that the most valuable work is being addressed.
- **Clear Acceptance Criteria**: Ensure every user story has clear and concise acceptance criteria before moving it to the **Develop** phase.
- **Assign Responsibility**: Always assign the user story to an appropriate team member at each stage to maintain accountability.
![image.png](/.attachments/image-4bcc25a9-52d7-4234-9a47-781317bb9306.png)
- **Update Status**: Regularly update the status and board placement of user stories to reflect their current state accurately.
![image.png](/.attachments/image-5649559b-de94-4b39-b8c5-b1c8bb9d6dac.png)
- **Review Done Items**: Periodically review items in the **Done** board to ensure they meet the Definition of Done (DoD) and gather feedback for continuous improvement.

### Conclusion

Managing user stories effectively through Azure DevOps Boards ensures a streamlined workflow and improves team collaboration. By following the above guidelines, you can enhance the efficiency of your project management process and deliver high-quality software.
