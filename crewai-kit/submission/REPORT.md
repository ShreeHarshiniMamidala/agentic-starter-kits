# CrewAI Assignment — Agent Modification and Output Comparison

## 1. Introduction

For this assignment, I worked with a CrewAI multi-agent system consisting of a Research Analyst, Technical Writer, and Editor. The goal was to understand how changing an agent's instructions could influence the final output of a collaborative AI workflow.

I selected the topic **"How AI helps detect potential drug side effects"** because it connects with my interest in healthcare AI and pharmacovigilance.

I completed two runs using the same topic and the GPT-OSS 20B model through Groq. In the first run, I used the original agents. In the second run, I modified only the Writer agent's role, goal, and backstory.

## 2. Original Agent — Run 1

The original Writer had the following configuration:

- **Role:** Technical Writer
- **Goal:** Explain the topic to a smart reader outside the field.
- **Backstory:** Turn dense technical material into clear, jargon-free prose.

The generated explanation focused on how AI analyzes electronic health records, clinical notes, chemical information, and other sources to identify potential drug safety concerns.

It also discussed techniques such as natural language processing, deep learning, and Bayesian networks.

Although the explanation contained useful technical information, it used specialized terminology that might be difficult for readers without a healthcare or data science background.

## 3. Modified Agent — Run 2

For the second run, I changed the Writer agent into a **Healthcare AI Explainer**.

The modified agent was instructed to explain healthcare AI using simpler language and relatable examples. I also asked it to distinguish suspected drug safety signals from confirmed side effects, discuss AI's limitations, and emphasize the importance of human oversight.

The Research Analyst and Editor agents remained unchanged.

The modified output used a more structured presentation, including numbered sections, a comparison table, and a separate discussion of human oversight.

## 4. Comparison of Results

The biggest difference between the two outputs was how the information was presented.

**Clarity and readability:** The original explanation was more technical and written primarily in paragraphs. The modified explanation used headings, numbered points, and analogies, making it easier to follow.

**Healthcare safety:** The modified explanation explicitly distinguished between a suspected safety signal and a confirmed side effect. This was an important improvement because identifying an unusual pattern does not automatically prove that a medication caused a medical problem.

**Human oversight:** The modified output gave greater attention to the role of healthcare professionals in reviewing AI-generated findings. It explained that AI can identify patterns but cannot independently establish clinical causation.

**Limitations:** Both outputs included `[source needed]` placeholders instead of complete scientific references. The modified output also retained technical terms such as protein-ligand interactions and QT-interval prolongation. Therefore, the changes improved communication but did not fully eliminate jargon or guarantee factual verification.

## 5. Challenges Encountered

During execution, I encountered an error where CrewAI received an empty response from the language model. I tested the Groq API independently and confirmed that it could generate text successfully.

I also encountered a Windows Unicode encoding error when printing the final result in PowerShell. The generated Markdown file was saved successfully despite the terminal error. I addressed the printing issue by configuring Python's output streams to use UTF-8.

To make the comparison more consistent, I used GPT-OSS 20B for both the original and modified agent runs.

These challenges helped me understand the importance of separating API connectivity, agent execution, and terminal output issues when debugging an AI workflow.

## 6. What I Learned

This experiment showed me that an AI agent's role, goal, and backstory can influence the style, structure, and emphasis of its output.

The original Writer provided a technical overview, while the Healthcare AI Explainer presented the topic in a more accessible way and placed greater emphasis on patient safety.

I also learned that better prompting does not automatically guarantee accurate references, complete adherence to instructions, or the removal of technical jargon. AI-generated content still requires evaluation and human review.

## 7. Conclusion

Changing a single agent's instructions produced a noticeable difference in the final explanation without requiring changes to the overall multi-agent workflow.

The modified Writer was better suited to explaining healthcare AI concepts to a general audience, especially when discussing potential drug side effects and the need for human oversight.

This assignment demonstrated how agent customization can make multi-agent AI systems more useful for specific audiences while reinforcing the importance of evaluating their outputs carefully.