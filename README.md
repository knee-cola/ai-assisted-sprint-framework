# Intro
In this project we will be working on developing AI workflow

## Initial idea
The idea is to develop a workflow in which an AI agent would first create a sprint document (more on that later). Then based on info found in sprint document AI agent would implement the sprint.

So the workflow would be:
1. user instructs AI agent what should be done in a sprint
2. AI agent creates a "sprint document" (based on a "sprint document template" ... more on that later)
3. user reviews the created "sprint document"
4. user instructs AI agent to begin working on the sprint
5. AI agent works on the sprint until completion

To help with this workflow multiple documents will be needed.

First document is a "sprint document template", which has the function of achieving the following goals:
* AI agent should understand the general goal of the sprint
* the document should outline the current state of the software
* the document should outline the desired state of the software (the goal)
* the document should split sprint into smaller units of work (user stories), which can be independently developed and tested
  * each unit of work should have a status indicator: todo, in progress, done
* the document should contain technical instructions including code snippets and pattern examples to ensure that the AI agent faster converge to correct solution
* at the beginning there should be a sprint status indicator, showing current status of the spring (i.e. not yet started, implementing user story 3, documenting, done)

Template should be accompanied by a "how to use the template" document which would contain instructions on how the AI agent how the template should be converted into a concrete "sprint document":
* analyze user's description of the sprint
* go through crucial project files to get a better picture about the current state of the project
* split the work into logical units / user stories
* keep the generated instructions concise and consistent
* the generated document should lead to minimal implementation being implemented (no features out of what is expected should be implemented)

A third "sprint implementation guidelines" document should exist which would amend the generated document with instructions for AI agent on how it should implement changes described in the sprint document (generated from template). These instructions should contain information such as:
* git flow instructions (sprint should be carried out on a separate branch, each logical unit of work should be committed separately)
* AI agent should keep track of current status of the sprint by updating status indicators inside the sprint document
* coding style instructions etc.