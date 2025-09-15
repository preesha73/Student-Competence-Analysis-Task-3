<h2>AI for Education: Evaluating Open Source Models for Student Code Analysis</h2>
This repository contains my submission for the Python Screening Task focused on evaluating AI models for educational purposes. The goal was to research and propose how an open-source AI could be used to analyze a student's Python code and provide feedback that deepens their understanding.

<h2>The Challenge</h2>
The core task was to figure out if we can use existing, free AI models to do something more than just check if a student's code works. Could we use them to:
<ul>
<li>Analyze a student's Python code to find conceptual gaps?
</li>
<li>Ask smart questions that make the student think, instead of just giving them the answer?
</li>
<li>Pinpoint where their reasoning might be going wrong?
</li>
<li>Encourage real learning?
</li>
<li>This document outlines my research plan, my reasoning, and my findings.
</li></ul>
<h2>My Approach & Research Plan</h2>
<ul>
<li>My plan is all about being practical and taking things one step at a time. The goal is to find a model that's not just powerful, but also the right tool for the job.
</li>
<li>First, I'd go hunting for potential models on places like Hugging Face and GitHub. I'm looking for a few key things: it has to be free and open-source, it should be built for code (not just general chatter), it needs to be good at following specific instructions, and it should be small enough that we can experiment with it without needing a supercomputer. Based on a quick search, CodeLlama-Instruct looks like a fantastic starting point. It's built by Meta, designed specifically for code, and has a version made for conversations and instructions.
</li>
<li>Once I have a model, I need to test if it's actually any good for teaching. To do this, I'd create a small test. I'd gather about 15-20 real-world Python code snippets from beginners—some with common mistakes and others that work but could be better. Then, I'd write a "prompt template" to ask the AI for help, like: "You are a friendly Python tutor. Look at this code, find the main logical error, and ask the student a question that helps them find the mistake on their own." The final step is the most important: I'd have a human expert (like a Python teacher) review the AI's generated questions to see if they're genuinely helpful, clear, and encouraging.
</li></ul>
<h2>Core Reasoning & Findings</h2>
Here's a breakdown of my thinking on the key questions from the task.

<h4>🤔 What Makes a Good AI Tutor?</h4>
So, what makes an AI model a good "tutor" for code? It's not just about spotting typos. It needs to have three special skills:
<ul>
<li>Seeing the Big Picture: A good AI tutor needs to look at a student's messy for loop and understand that they're trying to sort a list. It has to connect the code to the core computer science concept behind it, so it can talk about things like efficiency (O(n^2)) instead of just syntax.
</li>
<li>Following Instructions (Like a Teacher): It needs to be a great listener. If we tell it, "Don't give away the answer," it has to stick to that. This ability to adopt a persona or a set of rules is what separates a helpful tutor from a simple answer key.
</li>
<li>Giving Relevant Advice: The feedback has to be about the specific code the student wrote. Generic advice isn't helpful. The AI needs to pinpoint the exact line or logical flaw and tailor its questions to that specific problem.
</li></ul>
<h4>🔬 How Do We Know if It's Actually Helping?</h4>
You can't just use an automated score to know if an AI-generated prompt is "meaningful." You need a human touch. My plan is to test it with a teacher-in-the-loop:
<ul>
<li>Create a "Gold Standard" Set: An experienced teacher would look at student code, identify the main issue, and write the "perfect" guiding question for it.
</li>
<li>Let the AI Try: We'd give the same student code to the AI and ask it to generate its own question.
</li>
<li>Score the AI's Work: The teacher would then score the AI's question on a 1-5 scale for things like:
</li>
<li>Did it spot the right problem? (Diagnostic Accuracy)
</li>
<li>Does it make the student think? (Socratic Value)
</li>
<li>Is the question clear and simple? (Clarity)
</li>
<li>Is the hint too easy or too hard? (Scaffolding)
</li></ul>
If the AI scores well on this rubric, we know it's generating truly meaningful, helpful prompts.

<h4>⚖️ The Big Trade-Offs: Smarter, Cheaper, or Clearer?</h4>
<ul>
<li>When you're working with these powerful AI models, you can't have it all. You're always juggling three things: how smart it is (Accuracy), how easy it is to understand why it does what it does (Interpretability), and how much it costs to run (Cost).
</li>
<li>Smarter vs. Cheaper: The biggest, most powerful models (like a 70-billion parameter model) give amazing, nuanced feedback. But running them costs a fortune. A smaller model can run on a regular computer but might give more generic advice.
</li>
<li>Smarter vs. Clearer: The smartest models are "black boxes." They can give a brilliant answer, but we have no idea how they came up with it. A simpler, rules-based system (e.g., "if there's a loop inside a loop, warn about performance") is super clear and easy to understand, but it's nowhere near as clever or flexible as a big AI.
</li>
<li>Cheaper vs. Clearer: Usually, the easiest-to-understand systems are the cheapest to build and run. The most powerful "black box" AIs are the most expensive. You have to decide what's more important for your project.
</li></ul>
<h4>🚀 Why I Chose CodeLlama (And Its Pros & Cons)</h4>
I picked CodeLlama-Instruct as my primary model to evaluate. It's a fantastic open-source model from Meta that hits the sweet spot for this kind of educational task.

<h4>What's great about it? (Strengths 💪)</h4>
<ul>
<li>It Speaks "Code": It was trained on tons of code, so it has a deep understanding of programming languages like Python. It knows the difference between a rookie mistake and a clever shortcut.
</li>
<li>It's Designed to Chat and Instruct: The "Instruct" version is specifically fine-tuned to follow directions and have a conversation, which is exactly what we need for a tutoring bot.
</li>
<li>It's Flexible: It comes in different sizes. We can start with a small, cheap version to test things out and then scale up to a bigger, smarter version later if needed.
</li></ul>
<h4>What are the catches? (Limitations ⚠️)</h4>
<ul>
<li>It Wants to Give the Answer: The model is trained to be "correct," so its natural instinct is to just fix the student's code. We have to be very clever with our prompts to force it to be a guide instead of an answer key.
</li>
<li>It's Faking It (A Little Bit): CodeLlama doesn't actually understand teaching. It's just incredibly good at mimicking the patterns of helpful, educational text it saw during its training. This mimicry is powerful, but it can fail in unusual situations.
</li>
<li>It Can Be Wrong (With Confidence): Like any LLM, it can make stuff up or give incorrect explanations while sounding completely sure of itself. Any tool built with it would need a way for humans to double-check its work.
</li></ul>
