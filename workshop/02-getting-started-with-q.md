![Amazon Q Developer header](/images/q-vscode-header.png)

## Exploring Amazon Q Developer

Like all developer tools, it is worth spending some time to explore and see how they work to really maximise the benefit to your productivity. In this section we will cover at a high level what Amazon Q Developer provides you with, but I would encourage you to explore.

**Amazon Q Developer menu options**

When we click on the Amazon Q status bar link at the bottom of VSCode, we will see the following pop up. This provides you will access to Amazon Q Developer options, most of which you will not need whilst you are using it, but you will come back to do certain things. Let's go through what each of these options provides.

![amazon q developer menu options](/images/amazon-q-developer-plugin-menu.png)

* Pause Auto-Suggestions (Currently Running) - Amazon Q Developer provides you with suggested code blocks and snippets whilst working directly in your code. You can turn off this behaviour by clicking on this link (you will notice that it will then change to Resume Auto-Suggestions, Currently Paused, and the Amazon Q icon in the bottom status bar will also change). Every developer is different, and some prefer to have this option disabled, others enabled, so you will need to see what feels best for you. When paused, you can still invoke Amazon Q Developer to provide in-line code suggestions, by using the VSCode shortcuts (OPTION + C). Speaking of keyboard short cuts, lets check those out
* Open Code Reference Log - the underlying models that are used to power Amazon Q Developer use some open source code repositories, using Apache 2.0 and MIT licenced source files. Should code suggestions include portions from those projects, Amazon Q Developer will let you know by outputting this to the "Code Reference Log" which you can open by clicking on this menu option. When you click on this, you may see "Don't want suggestions that include code with references? Uncheck this option in Amazon Q: Settings". When using Builder ID you are not able to change this configuration, and the default option is to always include suggestions with code references. As you use Amazon Q Developer, check in here from time to time to see whether you are using code from those open source repositoires.
* Try inline suggestions examples - this provides a quick tutorial to walk you through the basics of how to use Amazon Q Developer inline suggestions
* Full Project Scan is now /review - this kicks off a /review of the current project. We will explore this in more detail later on in this tutorial
* Open Chat Panel - this will open up the Amazon Q Developer chat panel if you close it
* Send Feedback / Connect with us on GitHub / View Documentation - these options provide you with additional ways you can provide feedback if Amazon Q Developer is not working the way you think it should
* Open Settings - will open the Amazon Q Developer plugin settings options (as covered above)
* Sign Out (Connected as AWS Builder ID) - allows you to log out of your current session, with the identity displayed. During this lab, it will always be AWS Builder ID. 

---

**Keyboard shortcuts**

You can control how you invoke Amazon Q Developer via the various key shortcuts, including customising these to how you work.

![keyboard shortcuts for Amazon Q Developer](/images/q-vscode-view-keyboard.png)

One of the key short cuts to know when you are working in the inline editor, is the < and > arrows. These allow you to cycle through suggestions when you are prompted by Amazon Q Developer.

---

**Chat Interface**

You can open the Chat Panel by clicking on the Amazon Q status bar link at the bottom, which by default, will make it appear on the left hand side with the other application artifacts (like files open, git files, etc). You can drag the Chat Panel to the right hand side, as in the screenshot below, which I find helpful as it allows me to see my files in the project, the files I am editing, and then also provide me with my chat interface.

![Amazon Q Developer Chat interface](/images/q-vscode-screen-layout.png)

You can click on the + to open several chat sessions. When using Amazon Q Developer, the plugin will remember the conversations and use that in subsequent responses. This is very helpful when using Amazon Q to work through and troubleshoot issues. We will see this throughout this lab. You can open up to ten of these different tabs or conversations.

Amazon Q Developer also has some power features which are invoked using the /

* **/** brings up a list of the available commands. As Amazon Q Developer gains more capabilities, these will be displayed here
* **/clear** clears the current chat window conversation history, which is useful if you find the responses becoming circular or you want to reset the conversation context
* **/dev** invokes the Amazon Q Developer Agent for software development, and with this, it can create files, add new features, add tests, create documentation, and more. This is one of the most powerful features of Amazon Q Developer, as it will start to take your prompt, break it down into tasks, and then start working through the different tasks in realtime. It explores the files in your workspace to understand your project, and it will share which files it has reviewed and used, files it might want to change, and any new files it has created. Once finished, you will be able to review, check, and if desired, accept these updates.
* **/transform** invokes the Amazon Q Developer Agent for transformation that helps you migrate Java 8 projects to Java 17, taking the effort out of modernising your applications. We will not be using that during this lab, but it is worth knowing about if you are working with old Java applications.
* **/review** invokes the Amazon Q Developer Agent that will perform a review of the current project. This replaces the Security Scan feature that used to be in the Amazon Q Developer plugin
* **/doc** invokes the Amazon Q Developer Agent that will generate README's for your project, allowing you to create or update a README file so that you can keep your project documented
* **/test** invokes the Amazon Q Developer Agent that generates unit tests against functions. This currently only works for Java and Python code.

**Note!** When using /dev and /transform with Builder IDs, you have limited quota. You can find out more on the official [Amazon Q Developer pricing page](https://aws.amazon.com/q/developer/pricing/), if you scroll half way down you will see a table which outlines the limits you have open to you.

---

**Menu bar integration**

When you are working on our code within the editor, Amazon Q Developer provides a handy way to quickly invoke it to perform a number of functions. When working on a file, you can select a portion of code, or even if you want the whole thing, and then when you RIGHT CLICK, you will see an "Send to Amazon Q" menu option, which when you select you will see a number of options:

![Amazon Q Developer editor menus](/images/q-vscode-editor-menu.png)

* Explain - this will send whatever you have highlighted to the Amazon Q Chat panel, and ask Amazon Q to help explain what this code does
* Refactor - this will review the snippet and suggest ways you can improve code readability or efficiency, among other improvements
* Fix - this is handy if you are seeing linting errors in your code, or are trying to resolve other issues with your code
* Optimise - this will look to see if it can optimise the performance of the code you have selected
* Generate Tests - this will take the current function or class that you have highlighted, and then invoke the /test from within the chat interface. It wil then walk you through the steps for generating units tests for that function or class
* Send to Prompt - this will copy the portion you have selected and then move it to the Amazon Q Developer Chat Panel. You can then provide your own prompt to ask Amazon Q Developer what you want it to do. This is an easier way than copy/pasting the code snippet yourself.
* Inline Chat - this will bring up a small dialog box within the file you are editing, allowing you to enter a prompt. Amazon Q will then generate some code, asking you to then accept or reject it (hitting Enter to accept, or ESC to reject)

![Example inline chat window](/images/q-vscode-inline-chat.png)
![Example inline chat response](/images/q-vscode-inline-chat-example.png)

---

**Amazon Q Developer logs**

You can access the various Amazon Q Developer plugin logs from the OUTPUT menu option that appears when you have the terminal section in VSCode. When you select the pull down menu, you will see Amazon Q and Amazon Q Logs. The latter provides detailed information about how the plugin is working and interacting with the backend generative AI services powered by Amazon Bedrock.

---

**Workspace Indexing**

Amazon Q Developer allows you to index your local workspace which can then be used as part of the context when using the Chat interface. This is a very powerful feature that allows you to bring in additional information to help steer the direction of the output from Amazon Q Developer. For example, maybe you have some existing coding standards you want to influence any code that is generated by Amazon Q. Another way that you can use this is to help personalise the kind of output that Amazon Q Developer generates. You will see some examples of this in the .qdeveloper folder. There are two files, once called "java-expert.md" and the other "opensource.md". These contain additional prompts that will shape the output. A common way you can use this is to create shorter output, perhaps just outputing the code rather than any explaination.

You use this feature from within the Amazon Q Developer Chat interface. You invoke it with @ which will then display the available options. Currently this is only @workspace.

To use @workspace however, you need to first set this up. From the Amazon Q Developer plugin settings, you will see some new options.

![Amazon Q Developer plugin configuration options to enable workplace indexing](/images/q-workspace-settings.png)

Once enabled you will need to restart VSCode. When you restart it, from the OUTPUT tab, you will be able to see the output from the Workspace Index by checking out the Amazon Q Logs

```
2025-02-13 18:05:35.784 [info] LspController: LSP already installed
2025-02-13 18:05:36.022 [info] [Info  - 18:05:36] LSP server starts
2025-02-13 18:05:36.214 [info] [Info  - 18:05:36] Loaded model from /Users/ricsue/.vscode/extensions/amazonwebservices.amazon-q-vscode-1.46.0/resources/qserver
2025-02-13 18:05:36.357 [info] [Warn  - 18:05:36] Unknown tokenizer class "CodeSageTokenizer", attempting to construct from base class.
2025-02-13 18:05:36.415 [info] [Info  - 18:05:36] Device is not connected to power source. Set thread to 1.
2025-02-13 18:05:36.415 [info] [Info  - 18:05:36] Using number of intra-op threads: 1
2025-02-13 18:05:36.663 [info] [Info  - 18:05:36] Embedding provider initialized.
2025-02-13 18:05:36.668 [info] LspController: LSP activated
2025-02-13 18:05:36.668 [info] LspController: Starting to build index of project
2025-02-13 18:05:36.758 [info] LspController: Found 18 files in current project /Users/ricsue/Projects/amazon-q/workshop-2025/amazon-q-developer-hands-on
2025-02-13 18:05:36.768 [info] [Info  - 18:05:36] start building bm25 index
```

depending on how big your project is, this might take some time. When it has finished, you will see a message in the logs.

```
2025-02-13 18:05:57.838 [info] [Info  - 18:05:57] Vector indexing done for 15/18 files
2025-02-13 18:05:58.842 [info] [Info  - 18:05:58] Vector indexing done for 16/18 files
2025-02-13 18:06:02.106 [info] [Info  - 18:06:02] Vector indexing done for 17/18 files
2025-02-13 18:06:02.106 [info] [Info  - 18:06:02] Vector index complete! Take 25.156545917s. Total 18 files, 63 chunks
2025-02-13 18:06:02.106 [info] [Info  - 18:06:02] Vector index saved to /Users/ricsue/.aws/amazonq/cache/cache/b34d763123948282822a796f54a637adac670c8b30f241c6a4c21195679dde96-0.9-VSCode.index
```

One the indexing has completed, @worksplace will be ready to go.

As you update/delete files, the index is automatically updated.

```
2025-02-13 18:01:24.084 [info] Refreshing indexes...
2025-02-13 18:01:24.085 [info] [Info  - 18:01:24] Finished parsing 9 python files. Time 30.98ms
```

---

## Amazon Q Developer

Amazon Q Developer provides a number of useful tools, but you might be wondering which one should I use? The answer is that this depends on the kind of activities that you are doing. Here are some things to consider that will help you decide for a given activity what might be the right tool.

**Which Amazon Q Developer tool should I use?**

Which tool use use depends on a number of factors:

* What context can each tool use (file vs project)
* The difference in speed and developer experience, using inline editing is faster and more intuitive for developer
* The different Amazon Q developer capabilities have limits and quotas, so use when they are most impactful
* The amount of effort a task needs is a consideration. For example, you might want to make large or big changes to your project, where the effort to do this manually would be significant
* Are you learning something vs want to go faster? Chat tends to work great for learning new areas, where as inline works great for boosting productivity

We will learn more about this in the next lab.

---

### Amazon Q Developer - Guardrails

In this last section we take a look at something that you are probably going to encounter as you use Amazon Q Developer - the [AWS Responsible AI Policy](https://aws.amazon.com/machine-learning/responsible-ai/policy/).

Occasionally as you use and interact with Amazon Q Developer in any of the different modalities (chat, /dev, @workspace, or in-line), the output may come to an stop and you will be greeted a message.

![Guardrail message one](/images/q-vscode-guardrail.png)

The message might take other forms, for example with an error popup appearing in the bottom right of VSCode.

![Guardrail tripping](/images/q-vscode-error.png)

If you do encounter these, then try:

* adjusting the prompt - use different words, change the order
* test this against different files in your repo - sometimes it can be just one file that trips the guardrails, so you can narrow down where Amazon Q is tripping up
* review the Amazon Q Logs to see if you can find any information that might help you identify the root issue

The guardrails provide important protection for users of Amazon Q, and the tension between what will work and what trips them is changing all the time.




### Getting hands on in the sandbox

Let's try some of these out now in the next lab which will walk you through how these work in detail. [Practicing with Amazon Q Developer](03-sandbox.md)


