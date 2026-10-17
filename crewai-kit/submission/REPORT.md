# CrewAI Build Report

**Name:** Shree Harshini Mamidala  
**Topic I used:** How AI helps detect potential drug side effects

## 1. What I changed

For this assignment, I worked with the CrewAI starter kit and modified the Writer agent in `crewai-kit/main.py`. The original agent was called **Technical Writer**, and its goal was to explain a topic clearly to someone outside the field.

I changed its role to **Healthcare AI Explainer** because my topic focuses on identifying potential drug side effects using artificial intelligence. I wanted the explanation to be understandable to someone without a healthcare or technical background.

I updated the agent's role, goal, and backstory. The new instructions asked the agent to use relatable examples, explain the difference between a suspected safety signal and a confirmed side effect, and emphasize why healthcare experts must review AI findings. I also instructed it to avoid inventing statistics and scientific references.

I kept the Research Analyst and Editor agents unchanged so I could observe how modifying the Writer influenced the final explanation.

## 2. How CrewAI works

CrewAI is a framework that allows multiple AI agents to work together on a shared objective. Instead of asking one AI model to complete everything, CrewAI divides the work among agents with different responsibilities.

In my project, the **Research Analyst** gathers and organizes information about the topic. The **Writer** uses that information to create an explanation, and the **Editor** reviews the explanation to improve its clarity and quality.

Each agent has a role, goal, and backstory that guide how it approaches its work. A **task** defines what an agent is expected to produce, while a **crew** brings the agents and tasks together into a coordinated workflow.

The crew executes the tasks sequentially, so the output from one stage can provide context for the next stage. This allows the agents to collaborate instead of working independently.

My modification worked because the Writer received more specific instructions about its audience and the type of explanation it should produce. Even though the overall workflow stayed the same, the Writer approached its task differently.

This helped me understand that an agent's configuration can influence the final result without changing the structure of the entire multi-agent system.

## 3. Evidence

I compared the outputs from two executions using the same topic and GPT-OSS 20B model.

**Run 1 — `submission/explainer_run1.md`:**

The original Technical Writer produced a research-oriented explanation. It discussed electronic health records, natural language processing, deep learning, and Bayesian networks. The information was presented mainly in paragraphs and included technical terminology such as cardiotoxicity and pharmacovigilance.

**Run 2 — `submission/explainer_run2.md`:**

The modified Healthcare AI Explainer produced a more structured explanation with headings, numbered sections, and a comparison table. It explicitly explained the difference between suspected safety signals and confirmed side effects and emphasized the importance of human oversight.

The second output was easier to navigate, although it still contained some technical terminology.

**What went wrong:**

During execution, I encountered an error where CrewAI received an empty response from the language model. I tested the Groq API independently to confirm that it could generate responses. I also encountered a Windows Unicode encoding error while printing the final output. I addressed this by configuring Python's output streams to use UTF-8.

Both outputs also contained `[source needed]` placeholders, showing that the generated claims required further verification.

## 4. Choosing a framework

I would choose CrewAI for a project like this because it makes it easy to organize different responsibilities among specialized AI agents.

For example, in a healthcare AI project, one agent could collect and summarize drug safety information, another could interpret potential safety signals, and another could explain the findings to healthcare professionals. CrewAI provides a straightforward way to assign these responsibilities through agent roles, goals, and tasks.

One advantage I noticed was that I could change the Writer's behavior without redesigning the entire workflow. This makes CrewAI useful for projects where multiple agents collaborate to produce a final result.

Another framework we discussed in class is **LangGraph**. LangGraph would be useful if I needed more detailed control over the workflow, including conditional decisions, loops, or repeated evaluation steps.

However, for this assignment, LangGraph would likely require more explicit workflow design. CrewAI was easier to use because the starter kit already organized the agents and tasks into a sequential process.

I would prefer CrewAI for a straightforward collaborative workflow and consider LangGraph when a project requires more complex decision-making or customized execution paths.

## 5. Verification and AI use

I verified the results by reviewing both generated Markdown files and comparing their structure, terminology, and explanations.

I checked whether the modified output followed the new Writer instructions, particularly whether it explained suspected safety signals, distinguished them from confirmed side effects, and included human oversight.

I also checked the terminal logs to confirm that the workflow generated output files successfully. To troubleshoot the language model errors, I tested the Groq API independently and verified which model was being used.

Because the starter kit does not have web access, its agents generated information using the language model's existing knowledge rather than retrieving current scientific sources. Both outputs contained `[source needed]` placeholders. I therefore treated the scientific claims as unverified rather than assuming they were correct.

I used ChatGPT to help troubleshoot CrewAI execution errors, adjust the model configuration, resolve terminal encoding issues, and organize the comparison report. I verified the technical suggestions by running the commands in Cursor and examining the generated outputs and logs.

This assignment reinforced the importance of evaluating AI-generated explanations rather than relying on them without review.