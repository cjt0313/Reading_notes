# GPT 5 
1. Link: https://cdn.openai.com/pdf/8124a3ce-ab78-4f06-96eb-49ea29ffb52f/gpt5-system-card-aug7.pdf 
2. Arthurs and institution: OpenAI
3. 
## Key concepts
1. parallel test time compute, we refer to this as
gpt-5-thinking-pro
1. key features
   1. reducing hallucinations
   2. improving instruction following
   3. minimizing sycophancy
   4. level up performance in writing, coding, and health
2. data pipeline
   1. rigorous filtering to maintain data quality
   2. mitigate potential risks
   3. Moderation API and safety classifiers and to help prevent the use of harmful or sensitive content
3. safe completions
   1. focusing safety training on refusals can lead to brittleness for prompts with obscured user intent.
   2. a safety-training approach that centers on the safety of the assistant’s output rather than a binary classification of the user’s intent
   3. maximize helpfulness subject to the safety policy’s constraints
4. Sycophancy
   1. System prompts have a more limited impact on model outputs relative to changes in post-training
   2.  Using conversations representative of production data, we evaluated model responses, then assigned a score reflecting the level of sycophancy, which was used as a reward signal in training
   3. ![alt text](image.png)
5. Instruction Hierarchy
    1. Hierarchy: system > developer > user
6. Hallucinations
   1. goals
      1. training our models to browse effectively for up-to-date information
      2. On reducing hallucinations when the models are relying on their own internal knowledge.
   2. eval method
      1. using an LLM-based grading model with web access to identify major and minor factual errors in the assistant’s responses.
      2. validated the quality of this grader by having humans independently assess the correctness of claims extracted by the grader
      3. we employ OpenAI o3 as a grader in a two step process:
         1. OpenAI o3 lists all factual claims from the response that are relevant to the prompt
         2. we group claims into batches of 10 and provide each batch, together with the original prompt and response, to an instance of OpenAI o3, which uses its browsing tool to fact-check each claim and mark it as true, false, or unsure
7. Deception
   1. is learned from pre-training and post training
   2. may learn to be overconfident, cheat, or ‘trick’ fallible graders, even if their internal reasoning indicates uncertainty, as successful attempts garner a high reward.
   3. problems
      1. agentic coding: unresolvable impediments
      2. broken tools
      3. underpsecifed user request
         1. user asking a question about an image, but the image is not available
   4. monitoring a reasoning model’s chain of thought (CoT) was highly effective at detecting misbehavior while training reasoning models
8.  Red Teaming & External Assessments
   1. Purpose
      1. contribute to a specific hypothesis related to gpt-5-thinking’s safety
      2. measure the sufficiency of our safeguards in adversarial scenarios
      3. provide strong quantitative comparisons to previous models
   2. 9,000 hours of work from 400+ testers
   3. violent attack planning
      1. Red Teamers created conversations that generates responses from gpt-5-thinking and OpenAI o3 in parallel, with both models anonymized. 
      2. Red teamers then provided comparison ratings on each model’s generations throughout each conversation, and a detailed assessment when they chose to conclude the conversation.
   4. Prompt Injections
      1. Definition: Cybersecurity exploit where malicious actors manipulate the input prompts of (LLMs) to make them behave in unintended or harmful ways
      2. Microsoft automated red-teaming with Python Risk Identification Toolkit (PyRIT)
9.  Preparedness Framework
    1. OpenAI’s approach to tracking and preparing for frontier capabilities that create new risks of severe harm
    2. Safeguard design
       1. we developed an end-to-end suite of safeguards specifically to address the risks of severe harm identified in our externally validated threat model


## Related Works
### The Instruction Hierarchy: Training LLMs to Prioritize Privileged Instructions
1. Links: https://arxiv.org/pdf/2404.13208
2. Contributions
   1. Propose an instruction hierarchy that explicitly defines how models should behave when instructions of different priorities conflict.
   2. We propose an automated data generation method to demonstrate this hierarchical instruction following behavior, which teaches LLMs to selectively ignore lower-privileged instructions.
   3. We apply this method to LLMs, showing that it drastically increases robustness—even for attack types not seen during training—while imposing minimal degradations on standard capabilities.
   4. ![alt text](image-1.png)
#### Key concepts
1. Context Synthesis: 
   1. For Aligned instructions, we generate examples using an approach we denote context synthesis
   2. We take compositional requests and decompose the instructions into smaller pieces.
   3. We then place these decomposed instructions at different levels of the hierarchy and train models to predict the original ground-truth response.
2. Context Ignorance
   1.  For Misaligned instructions, we use the exact opposite approach: we train models to predict the same answer they would have generated if they never saw the lower-level instructions.
3.  While creating this data, we strike a careful balance not to trigger overrefusal behavior, where a model refuses to comply even when a low-priority instruction was aligned
4.  ![alt text](image-2.png)
5.  Direct Prompt Injections for Open-domain Tasks
    1. we create Aligned instructions using context synthesis.
         1. We first prompt an LLM to generate compositional requests (e.g., ”write a 20 line poem in spanish”), and ask it to decompose the instructions into smaller pieces (e.g., ”write a poem”, ”use spanish”, ”use 20 lines”). 
         2. We place the decomposed instructions into different levels of the hierarchy, and train models to produce the same response as if
         they saw the entire compositional instruction in the system message.
   1. For Misaligned instructions, we train models using context ignorance for handling these instructions.
   2. we first prompt a model to generate various system messages that contain different types of rules or constraints (e.g., “never give legal advice”). We then generate user queries that adversarially trick the model into breaking one of the imposed rules.
6. Direct Prompt Injections for Closed-Domain Tasks
   1. We argue that there are no Aligned instructions for closed-domain tasks
   2. ![alt text](image-3.png)