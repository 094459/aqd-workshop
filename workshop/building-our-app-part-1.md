![Amazon Q Developer header](/images/q-vscode-header.png)

## Building our application - Part One

**Overview**

In the first part of this lab we are going to start by first looking at the data model for our application. As we are building a customer survey feedback application, we want to spend some time thinking about how to craft the right prompts.

**Creating our Python Virtual Environment**

If you have VSCode currently running, close and exit as we will be creating a clean environment to begin this tutorial.

From a terminal, navigate to a new directory where we will start work (I am using projects here as this is what I use, but feel free to switch this to whatever you use), and then type in the following. 

```
cd ~/projects
mkdir handson-amazon-q
cd handson-amazon-q
code .
```
This will start VSCode in this directory.

Once VSCode has started, the first thing we need to do is make sure that we are running in the Python virtual environment we created. Open up a Terminal in VSCode, and from that terminal run the following commands:

```
python -m venv .venv
source .venv/bin/activate
```

You should notice that the Terminal inside VSCode now has the (.venv) prefix, indicating you are running in this new virtual Python environment.

You should also switch your VSCode Python environment to use this. From VSCode press CTRL + COMMAND + P (Mac), or CTRL + SHIFT + P (Windows) and type in Python. From the list, select "Select Interpreter" and from the available options, make sure you select the one which has the correct directory location (.venv) which should be the recommended one. 

![Selecting Python interpreter](/images/q-vscode-python-env.png)

**Adding a .gitignore file**

As you build out your project, Amazon Q Developer references the .gitignore file (if it exists) to help it optimise what files it will look for. This is super helpful for example, when you want to ignore certain files or directories you have in your project that might influence the outputs. We can use Amazon Q Developer to help us create this file.

1. Create a new file in this project called ".gitignore" (you can create this via the IDE or via the command line)
2. Open up the .gitignore file in VSCode (it will be empty)
3. Either from right clicking and selecting "Amazon Q > Inline chat" or by using the keyboard shortcut (COMMAND + I) enter the following

> Add entries into this .gitignore file for a typical Python project

It should quickly start adding entries and then prompt you to review/accept. Accept and then save the file.

You are now ready to go.

---

**Creating our application - Creating our Data Model**

The application we want to build is a simple tool for collecting customer feedback. We are going to start by using Amazon Q Developer to help us define the data model for this application, providing various prompts that will help provide a good starting point of what we want our data model to look like. Once we have our data model, we can then start to create some code artefacts.

A key pattern of working with AI coding assistants like Amazon Q Developer is to take some time to articulate what you want them to do. In this instance, we want Amazon Q Developer to create our data model. 

> **Tip!** When doing this in real life, do not just make it up on the fly! Take some time to think about how to formulate it. The more you use tools like Amazon Q Developer, the more natural and easier it will get

**Task 1**

1/ The data model is a reflection of the User requirements of the application. For this simple customer feedback application, we might use the following to describe this.

*"Create a data model for a simple customer survey application. Users will log in using an email addresses. Users will be able to create new surveys, or update/delete existing surveys. Users can create multiple surveys. Surveys can have between 2 and 5 options. Once a Surveys is created, the End Users will be able to submit feedback"*

2/ AI Coding Assistants can help turn this into code. Using the chat interface of Amazon Q Developer, enter the above into the chat interface and hit enter:

> Create a data model for a simple customer survey application. Users will log in using an email addresses. Users will be able to create new surveys, or update/delete existing surveys. Users can create multiple surveys. Surveys can have between 2 and 5 options. Once a Surveys is created, the End Users will be able to submit feedback.

Give the non deterministic nature of these tools, it is hard to predict the output you will get! Review the output - does it make sense? What is it missing? How would you improve it? Or perhaps, it did a good job and you are happy about it. As you use these tools more, you should be constantly reviewing the ouput. Do **NOT** assume that the ouput is always going to be right.

**Task 2**

We are going to now try again, and this time use a feature of the Amazon Q Developer that will help us personalize the output that we get. From the project workspace, we are going to create a file which will then be used as context by Amazon Q, and help shape the output. 

1/ We need to create a file that Amazon Q Developer will use as context, so follow these steps:

1. In the project directory create a folder called ".qdeveloper"
2. Create a new file in this directory called - DBA.md (you can call it something different, the file name is not that important)
3. Add the following text within this file, and then save it

```
DBA

Only when I explicitly ask for code, follow this guidance:

- Only provide SQL code unless I explicitly ask for another language
- I am an expert in SQL and I did not need a walk through
- I have a strong preference for Sqlite
```

We are going to use this file as additional context when prompting Amazon Q Developer. We are defining our particular style (for this workshop). You can use this technique yourself, changing it to suit what you want. For this workshop we are going to keep this.


So our project directory structure will look like

```
├── .qdeveloper
│   └── DBA.md
└── .venv

```

3/ Make sure you have closed all the open files/tabs in VSCode. From the Amazon Q Developer Chat interface, type @ and you should see workspace appear. Tab to complete that, and then add the following to your prompt:

> @workspace DBA Create a data model for a simple customer survey application. Users will log in using an email addresses. Users will be able to create new surveys, or update/delete existing surveys. Users can create multiple surveys. Surveys can have between 2 and 5 options. Once a Surveys is created, the End Users will be able to provide feedback.

Hit return and review the output. How was the output different? 

4/ You can use this technique to help provide more consistent output that is in line with how **YOU** want to work.

---

**Task 3**

Now that we have seen how to tailor the output we get from Amazon Q Developer, we are going to show another way we can produce the data model. From within the file itself, using the inline capabilities of Amazon Q Developer. We will show how you can do this for both SQL and Python.

1/ Close any files/tabs you might have open. From VSCode create a folder called **"data"** and create a new file called **"customer-feedback.sql"**.

2/ Ensure the cursor is at the top of the page, and then press COMMAND + I which will bring up the inline prompt. When we use the inline capabilities we cannot rely on the additional context, so we have to be explicit. Enter the following and then hit return.

> Create a data model for a simple customer survey application. Users will log in using an email addresses. Users will be able to create new surveys, or update/delete existing surveys. Users can create multiple surveys. Surveys can have between 2 and 5 options. Once a Surveys is created, the End Users will be able to submit feedback.

As we have create the file called **"customer-feedback.sql"** Amazon Q Developer is smart enough to know that we are going to be wanting SQL code.

Review the output. How does it compare with the code produced from the chat interface? Press ESC to ignore the code suggestions, and make sure the file is blank. Save the file (so that you have an empty file called "customer-feedback.sql").

3/ Close the file/tab, and this time from the root folder in VSCode, create a new file called **"app.py"**. Open this file within the editor, and repeat the same step as previous. This time we will generate the prompt using comments. At the top of the page, add the following:

```
"""
Create a data model for a simple customer survey application. 
Users will log in using an email addresses. 
Users will be able to create new surveys, or update/delete existing surveys. 
Users can create multiple surveys. 
Surveys can have between 2 and 5 options. 
Once a Surveys is created, the End Users will be able to submit feedback.
"""
```

Hit return and wait - you should see Amazon Q Developer begin to think. Does it finish? What do you think of the output?

As we have create the file called "app.py" Amazon Q Developer is smart enough to know that we are going to be wanting Python code.

In both the previous example, we have seen how using different capabilities can have a big impact on the output produced, or whether any output is produced at all.

4/ Delete the contents of app.py file and save (so that it is an empty file).Close any other files/tabs you might have open. Re-do the same prompt from the Amazon Q Developer chat interface

> @workspace DBA Create a data model for a simple customer survey application. Users will log in using an email addresses. Users will be able to create new surveys, or update/delete existing surveys. Users can create multiple surveys. Surveys can have between 2 and 5 options. Once a Surveys is created, the End Users will be able to submit feedback. 

Review the SQL - does it look right?

Does it look different from the first time you ran it? Welcome to the world of non deterministic output. 

To simplify how we run this workshop, rather than copy your SQL code into the **"customer-feedback.sql"**, use the following code. Paste this code into the **"customer-feedback.sql"** file in the data directory.

```
-- Users table to store user information
CREATE TABLE Users (
    user_id INTEGER PRIMARY KEY AUTOINCREMENT,
    email TEXT UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_login TIMESTAMP
);

-- Surveys table to store survey information
CREATE TABLE Surveys (
    survey_id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER NOT NULL,
    title TEXT NOT NULL,
    description TEXT,
    is_active BOOLEAN DEFAULT 1,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id) ON DELETE CASCADE
);

-- Survey Options table to store the options for each survey
CREATE TABLE Survey_Options (
    option_id INTEGER PRIMARY KEY AUTOINCREMENT,
    survey_id INTEGER NOT NULL,
    option_text TEXT NOT NULL,
    option_order INTEGER NOT NULL,
    FOREIGN KEY (survey_id) REFERENCES Surveys(survey_id) ON DELETE CASCADE,
    CONSTRAINT check_option_order CHECK (option_order BETWEEN 1 AND 5)
);

-- Survey Responses table to store end user feedback
CREATE TABLE Survey_Responses (
    response_id INTEGER PRIMARY KEY AUTOINCREMENT,
    survey_id INTEGER NOT NULL,
    option_id INTEGER NOT NULL,
    respondent_email TEXT,
    response_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (survey_id) REFERENCES Surveys(survey_id) ON DELETE CASCADE,
    FOREIGN KEY (option_id) REFERENCES Survey_Options(option_id) ON DELETE CASCADE
);

```

Save the file, and we can now go to the next task in this lab.

---

**Task 4**

Generating code from our data model is a task well suited to AI Coding Assistants like Amazon Q Developer. Lets see quickly how we might generate Python code.

1/ Make sure that all the open files are closed EXCEPT the **"customer-survey.sql"** file. From the Amazon Q Developer chat interface, type in the following:

> Generate this data model in Python

Review the output. What are your thoughts?

2/ A common task that developers have to do is update code based on changes to the data model. Using Amazon Q Developer, this task is now simple and quick to do. Make sure that all the open files are closed EXCEPT the **"customer-survey.sql"** file.

Edit the sql code in the open file, amending the User model to add "alias TEXT NOT NULL" so it looks like the following.

```
CREATE TABLE Users (
    user_id INTEGER PRIMARY KEY AUTOINCREMENT,
    email TEXT UNIQUE NOT NULL,
    alias TEXT NOT NULL,
    password_hash TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_login TIMESTAMP
);
```

3/ Save the file, and then re-run the prompt from 1/

> Generate this data model in Python

Review the output. Did it update the Python code?

**Task 5**

AI Coding Assistants like Amazon Q Developer are very effective at helping you build SQL queries you can use within the applications you develop. Now that we have our data model in SQL, lets generate some queiries (we will not run them, but we can try again later once we have built the database)

1/ Make sure that all the open files are closed EXCEPT the **"customer-survey.sql"** file. 

2/ In a new chat window, try the following:

> how would I write a SQL query to get the most popular surveys
> How would I query to find out who has created the most surveys
> Create a sql query to show many total surveys and suvery submissions there have been

Review the output of the different prompts. 

---

**Task 6**

In this task we are going to see how we can generate diagrams from our SQL, as well as generate SQL from our diagrams. We will need to install a VSCode plugin if you do not already have this installed. From the VSCode marketplace, find the following plugin

![Enhanced Markdown Viewer](/images/vscode-markdown-enhanced.png)

You can use [this link](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)

This will provde you with a new option when you right click on any markdown document, as follows:

![Enhanced Markdown viewer](/images/vscode-markdown-enhanced-fileopen.png)


1/ Close all files/tabs in VSCode. Open up the **customer-feedbck.sql** file and from a new chat interface, add the following prompt:

> create a mermaid diagram of this sql code that I can display in a markdown doc

Review the output. In the same directory (data) create a new file called **"customer-feedback.md"** and add then copy the contents into the file. If you try and display this as it is, it will not work ( try it ). We need to add the markdown tag so that it knows to use the Mermaid diagram extension. If you are new to this, we can easily do this with the help of Amazon Q.

2/ Select all the code in the newly create file, and then use the Amazozn Q menu integration (right click, Amazon Q > Send to Prompt). From the prompt, enter the following:

> Add the markdown to display this

After a while you should see some updated code. Overwrite the contents with the output from the chat inteface (after reviewing), and then try again with the enhanced Markdown preview. You should get something like this.

![documenting the application schema](/images/q-erd.png)

Close all the tabs in VScode.

You can actually generate SQL code FROM mermaid diagrams (other diagram formats will work also, if they generate a text based format structure).

---

**Summary**

In this first section we have built up the data model for our application, and explored just a few of the ways that Amazon Q Developer, our trusted AI Coding Assistant can help speed us along in the work we do.

You can now proceed to [Part Two](/workshop/building-our-app-part-2.md).