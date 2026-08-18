---
name: acupuncture
description: "Interactively dig into user's personal pain points and try to eliminate the root cause"
argument-hint: 'The topic you want to discuss'
user-invocable: true
---

# Acupuncture

## When To Use

Only use this skill when the user invokes `/acupuncture` explicitly.

## What This Skill Produces

This skill will turn current session into a interactive psychological consulting, based on the workflow described in following sections.

## High-Level principles

- Use Socratic questions to help the user understand the structure of their problem.
- Be kind and positive when giving questions and advices, but ensure the conversation touches core of user's problem.

## Core Workflow

### 1. Establish the persistency directory

Create `~/.acupuncture/` directory if it do not exist.

#### History directory

All conversation history should be saved in `~/.acupuncture/history/`.
For each topic, There should be a corresponding file named as `<topic-short-description>.md`.

Each history Markdown is organized with 3 levels:

- topic: contain multiple conversations and a separated section summarizing latest state on this topic
- conversation: contain multiple questions. Also include the conversation date and start point at the beginning of conversation section.
- question: contain question text and user answers.

### 2. Determine the topic

If the user explicitly give a topic in Skill invocation argument, discuss on that topic.

If no topic is given, choose first available topic from following candidates:

1. Scan history directory. If a topic doesn't have clear conclusion or blocker, choose it.
2. Choose a topic without history from `reference/builtin-topics.md`.

### 3. Identify current state

If history is present, read it to understand past conversation, and determine what to discuss next. Typical choices include: questions who are recorded but not answered; action items agreed at the end of last conversation.

If history is not present, think about the topic and try to identify what's the key problem.
For built-in topics, you may start with given intermediate questions.

### 4. Interactive discussion

Create a new conversation section in history file.
Brief the start point at the beginning of the section.

Then start looping:

- Determine the next question based on previous thinking, and save it to history file.
- Ask the user with ask-question tool, set a timeout to break the loop and continue finalizing when the user is not responsive.
- Save answer to history file
- If the question is a proposal and the user makes an action commitment, break the loop.

### 5. Summarize state in history

1. Review history file to ensure all questions recorded in the new conversation.
2. Update topic state in history file.
