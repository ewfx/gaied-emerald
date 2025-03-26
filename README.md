# 🚀 Project Name

## 📌 Table of Contents
- [Introduction](#introduction)
- [Demo](#demo)
- [Inspiration](#inspiration)
- [What It Does](#what-it-does)
- [How We Built It](#how-we-built-it)
- [Challenges We Faced](#challenges-we-faced)
- [How to Run](#how-to-run)
- [Tech Stack](#tech-stack)
- [Team](#team)

---

## 🎯 Introduction
## A brief overview of your project and its purpose. Mention which problem statement are your attempting to solve. Keep it concise and engaging.
Our project aims to streamline the processing of commercial banking lending service requests by leveraging Gen AI-driven automation and using an AI agent to perform the task of gatekeeping which facilitates faster and smooth orchestration of service request mails to the appropriate team members based on the request and sub request type classified by the model. Our agentic workflow has been built using latest tools and models, where the workflow sits on n8n consuming Llama 3.2 90B Vision (Preview) model for activities such as summarization and classification and LlamaParse for OCR/ parsing of the documents and Airtable database for temporary storage of parsed outputs.



## 🎥 Demo
🔗 5 Videos uploaded
📹 PPT describing the solution and scenarios uploaded. Architecture diagram ppt also uploaded.



## 💡 Inspiration
What inspired you to create this project? Describe the problem you're solving.
Email/ Document traige and routing is a common problem across teams, organizations, etc. and automating it benefits multiple teams. Also, this is our first agentic AI project levergaing Gen AI models, embaling us to step into the AI bubble.

## ⚙️ What It Does
Explain the key features and functionalities of your project.
1. Classifies the email based on context and provides the following as output in a json format:
   a. Request type
   b. Sub-request type
   c. Confidence score
   d. Reasoning
   e. Numerical fields in the attachment
2. It will identify if the response is generic, redundant or irrelevant to the context, response to a previous request and mark them as duplicates
3. It will identify if the mail contains more than one service request and return both request types as output
4. It will classify irrelevamt mails as Other.
5. It will prioritize context of email content over that of attachments.

## 🛠️ How We Built It
Briefly outline the technologies, frameworks, and tools used in development.
1. The workflow is built using n8n workflow automation tool where the trigger is a polling of gmail account every minute for the arrival of a new mail.
2. The mail content and attachments ae then extracted and passed to LlamaParse.
3. A webhook response waits for an asynchronous response from LlamaParse.
4. LlamaParse outputs are temporarily stored in an Airtable table. Later it is cleared in the end of the process.
5. The email content and LlamaParse output are summarized to ensure that they are not very lengthy.
6. Finally the outputs are fed to the AI agent which uses Llama 3.2 90B Vision (Preview) model to accurately classify and provide output json with the details mentioned in the previous point.

## 🚧 Challenges We Faced
Describe the major technical or non-technical challenges your team encountered.
1. Understanding the capabilities and limitations of the n8n tool.
2. We had to generate our own test data, we feel the testing could have been effective if some sample mails were provided.
3. Understanding the business behind commercial loan offerings and the service requests that can be received.

   
## 🏃 How to Run
1. Download the content in the repository.
   
2. Import the 4 json files in the src folder in a n8n workflow.
  
3. Setup gmail credential, bearer token for LlamaParse, Groq API keys, Airtable bearer token for the AI model.

4. Activate all the 4 workflows.

5. Run the Email_AI_Agent, rest are auto triggered.
   
## 🏗️ Tech Stack
n8n, LlamaParse, Airtable

## 👥 Team
- Priyanka Subramanian
- Aditya Sinha
- Marimuthu Ramasamy
