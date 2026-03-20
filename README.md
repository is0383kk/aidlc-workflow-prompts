<table>
  <thead>
      <tr>
          <th style="text-align:center">English</th>
          <th style="text-align:center"><a href="./README_ja.md">日本語</a></th>
      </tr>
    </thead>
</table>

# AI-Driven Development Lifecycle (AI-DLC) Prompts

This repository contains prompts for product development following the "[AI-Driven Development Lifecycle (AI-DLC)](https://prod.d13rzhkk8cj2z0.amplifyapp.com/)" process proposed by Amazon Web Services.

- https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/

Prompt execution is designed with the assumption of **AI agent interaction such as Amazon Q developer CLI, Claude Code, GitHub Copilot CLI, or Codex CLI**.

# 1. Overview

This prompt collection consists of the following 5 phases:

1. **User Story Planning** - Define requirements as user stories
2. **Unit of Work Planning** - Break down user stories into implementable work units
3. **Domain Model Design Planning** - Design domain models for business logic
4. **Code Implementation Planning** - Implement source code from domain models
5. **Architecture Component Planning** - Build architecture to operate the implementations

## ■ Prompt Structure

```
├── 01-user-story-planning.md          # User story creation prompt
├── 02-unit-of-work-planning.md       # Work unit division prompt
├── 03-domain-model-planning.md        # Domain model design prompt
├── 04-domain-to-code-planning.md      # Code implementation prompt
└── 05-architecture-component-planning.md  # Architecture component creation prompt

```

# 2. Usage

## ■ Basic Work Flow

1. **Select Prompt**: Choose the prompt file according to the development phase
2. **Input to AI Assistant**: Input the selected prompt to the AI assistant
3. **Create Work Plan**: AI creates a work plan document
4. **Answer Questions**: Answer questions in the plan document
5. **Approve Plan**: Review and approve the work plan
6. **Step-by-Step Execution**: AI executes step by step according to the plan

## ■ Step 1. User Story Creation (`01-user-story-planning.md`)

**Role**: Product Owner  
**Purpose**: Create clear user stories for the target system

0. 【Option】Clear context
1. Describe what you want to create in `01-user-story-planning.md` and execute the prompt in the file
2. A work plan document for user story creation is created: `docs/inception/01-user-story/user-story-plan.md`
3. Answer and save the questions listed in `docs/inception/01-user-story/user-story-plan.md`
4. Instruct the AI agent to create user stories according to `docs/inception/01-user-story/user-story-plan.md`
5. Work breakdown files related to user stories are created in `docs/inception/01-user-story/result`

## ■ Step 2. Unit of Work Division (`02-unit-of-work-planning.md`)

**Role**: Software Architect  
**Purpose**: Divide user stories into work units that can be implemented in parallel

0. 【Option】Clear context
1. Execute the prompt in `02-unit-of-work-planning.md`
2. A work plan document for dividing user stories is created: `docs/inception/02-unit-of-work/units-plan.md`
3. Answer and save the questions listed in `docs/inception/02-unit-of-work/units-plan.md`
4. Instruct the AI agent to divide user stories according to `docs/inception/02-unit-of-work/units-plan.md`
5. User stories after work division are output to `docs/inception/02-unit-of-work/result`

## ■ Step 3. Domain Model Design (`03-domain-model-planning.md`)

**Role**: Software Engineer  
**Purpose**: Design domain models to implement user stories

0. 【Option】Clear context
1. Select the user story to be the target of domain model design (e.g., `unit1-task-creation.md`) and specify it as input in `03-domain-model-planning.md`
2. Execute the prompt in `03-domain-model-planning.md`
3. A work plan document for domain model design from user stories is created: `docs/construction/03-domain-model/domain-model-plan.md`
4. Answer and save the questions listed in `docs/construction/03-domain-model/domain-model-plan.md`
5. Instruct the AI agent to divide user stories according to `docs/construction/03-domain-model/domain-model-plan.md`
6. Domain model design documents are created in `docs/construction/03-domain-model/unitX/result`

## ■ Step 4. Implementation (`04-domain-to-code-planning.md`)

**Role**: Software Engineer  
**Purpose**: Implement source code from domain model design

0. 【Option】Clear context
1. Select the domain model design to be implemented (e.g., `docs/inception/03-domain-model/unitX/result/`) and specify it as input in `04-domain-to-code-planning.md`
2. Execute the prompt in `04-domain-to-code-planning.md`
3. A work plan document for implementation from domain model design is created: `docs/construction/04-domain-to-code/unitX/domain-to-code-plan.md`
4. Answer and save the questions listed in `docs/construction/04-domain-to-code/unitX/domain-to-code-plan.md`
5. Instruct the AI agent to divide user stories according to `docs/construction/04-domain-to-code/unitX/domain-to-code-plan.md`
6. Implementations are created from domain model design (e.g., `task_management`)

## ■ Step 5. Architecture Component Creation (`05-architecture-component-planning.md`)

**Role**: Software Architect  
**Purpose**: Add architecture components to operate the implementations

0. 【Option】Clear context
1. Select the target implementation directory (e.g., `task_management`) and specify it as input in `05-architecture-component-planning.md`
2. Select the target divided user story (e.g., `docs/inception/02-unit-of-work/result/unitX-XXX.md`) and specify it as input in `05-architecture-component-planning.md`
3. Execute the prompt in `05-architecture-component-planning.md`
4. A work plan document for architecture component creation is created: `docs/construction/05-architecture-component/architecture-component-plan.md`
5. Answer and save the questions listed in `docs/construction/05-architecture-component/architecture-component-plan.md`
6. Instruct the AI agent to create architecture components according to `docs/construction/05-architecture-component/architecture-component-plan.md`
7. Architecture components are created

# 3. Deliverable Structure

By executing the prompts, documents and implementations are generated in the following structure:

```
docs/
├── inception/                  # Planning and design phase
│   ├── 01-user-story/
│   │   ├── user-story-plan.md
│   │   └── result/
│   └── 02-unit-of-work/
│       ├── units-plan.md
│       └── result/
│           ├── unit1-*.md
│           └── unit2-*.md
├── construction/               # Construction phase
│   ├── 03-domain-model/
│   │   └── unitX/
│   │       ├── domain-model-plan.md
│   │       └── result/
│   ├── 04-domain-to-code/
│   │   └── unitX/
│   │       └── domain-to-code-plan.md
│   └── 05-architecture-component/
│       └── architecture-component-plan.md
│
└── Source Code + Architecture Components
```

