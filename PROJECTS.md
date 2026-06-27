# Projects

这份文档用于展示我围绕 **Agent Harness / LLM 工程 / 个人自动化** 做过的项目和实验。  
重点不是罗列所有仓库，而是说明这些项目分别证明了什么能力。

## Main Direction

我目前最关注的问题：

- Agent 如何组织任务循环、工具调用、上下文和记忆
- LLM 应用如何从 demo 变成可恢复、可观察、可维护的工作流
- 开发者如何与 Agent 协作：发起任务、查看过程、理解失败、恢复执行
- 个人真实任务如何作为 Agent Harness 的反馈源

## 1. Deep Reader

**Status**: local project, not public yet  
**Tech**: Python, DeepSeek OpenAI-compatible API, EPUB/TXT parsing, multi-agent workflow, Markdown output  
**Role**: independent project

Deep Reader is an AI reading companion for long-form books. It parses EPUB/TXT files chapter by chapter and runs a structured analysis pipeline:

```text
Book -> Chapter Parser -> Reader Agent -> Critic Agent -> ContextStore -> Markdown Notes
```

### What I Built

- EPUB/TXT chapter parsing with dry-run preview, skip/limit controls, and custom output paths
- Reader Agent for extracting core arguments, evidence, and low-information passages
- Critic Agent for adversarial review of logical gaps, hidden assumptions, concept drift, and alternative explanations
- ContextStore for cross-chapter memory using recent summaries, cumulative summaries, and compressed chapter notes
- chapter-level logging, retry handling, failure recording, and resumable processing
- Markdown rendering for per-chapter notes and full-book index

### Why It Matters

This project is close to Agent Harness problems:

- It separates task roles instead of using one large prompt for everything.
- It manages long-context pressure through structured memory rather than raw history concatenation.
- It treats failure, resume, logs, and outputs as first-class workflow concerns.
- It uses a real reading task to observe model behavior in extraction, critique, and context retention.

### Next Improvements

- publish a cleaned public repository
- add tests around chapter parsing and ContextStore behavior
- add a trace view for Reader/Critic inputs and outputs
- compare different memory compression strategies

## 2. Telegram AI Bot

**Repository**: [theman6660/telegram-ai-bot](https://github.com/theman6660/telegram-ai-bot)  
**Tech**: Node.js, Telegram Bot API, Gemini API, GitHub API, Railway, Docker  
**Role**: independent project

A Telegram bot for personal AI interaction and workflow automation.

### What I Built

- Telegram polling bot based on `node-telegram-bot-api`
- Gemini API integration with configurable model and proxy support
- deployment workflow with Railway / Docker instructions
- local memory and daily snippet collection
- GitHub API integration for pushing structured snippets to a website repository
- support for voice-related dependencies through Edge TTS and ffmpeg

### What It Demonstrates

- connecting LLM behavior to an actual messaging interface
- managing environment variables, deployment, logs, and runtime dependencies
- turning chat interaction into downstream automation, not just conversation
- integrating user input, model output, local state, and GitHub updates

### Agent Harness Relevance

The bot is an example of a small but real harness: message input, model call, state storage, tool-like GitHub operations, and feedback to the user all live in one loop.

## 3. Personal Website Automation

**Source Repository**: [theman6660/beifen](https://github.com/theman6660/beifen)  
**Generated Site Repository**: [theman6660/theman6660.github.io](https://github.com/theman6660/theman6660.github.io)  
**Website**: [hanxiaofan.site](https://hanxiaofan.site)  
**Tech**: Hexo, JavaScript, GitHub Actions, DeepSeek API, RSS, GitHub Pages  
**Role**: independent project

This is my personal site and automation system. The source repo contains the Hexo site, daily content generation scripts, AI chronicle utilities, and recovery documentation.

### What I Built

- Hexo + Redefine based personal website
- AI daily report generation script using RSS sources and DeepSeek-compatible API
- social thought daily generation script
- AI chronicle update utilities for maintaining a long-running timeline article
- GitHub Pages deployment flow
- rollback and recovery documentation separating source truth from generated output

### What It Demonstrates

- using LLMs inside a publishing workflow instead of isolated prompting
- building guardrails around automated content generation
- thinking about deployment, rollback, source-of-truth, and generated artifacts
- maintaining a public-facing site with recurring automation

### Agent Harness Relevance

This project gives a real feedback source for automation reliability: scheduled tasks can fail, generated files may conflict, deployment can drift from source, and recovery needs explicit tooling and documentation.

## 4. Escher Droste Tool

**Repository**: [theman6660/escher-droste-tool](https://github.com/theman6660/escher-droste-tool)  
**Demo**: [hanxiaofan.site/escher-droste-tool](http://hanxiaofan.site/escher-droste-tool/)  
**Tech**: HTML, CSS, JavaScript, WebGL, image processing  
**Role**: independent project

A single-page browser tool for transforming images into Droste / Escher-style recursive spatial effects.

### What I Built

- WebGL real-time rendering pipeline
- image upload and preview
- multiple mapping modes, including complex-exponential style mapping and circular periodic mapping
- adjustable scale, rotation, center point, global zoom, and edge mode
- PNG export from current rendered canvas
- README with usage notes, recommended parameters, and technical explanation

### What It Demonstrates

- ability to build a polished interactive tool without a heavy framework
- practical graphics programming and parameterized visual exploration
- writing user-facing documentation for a technical tool

## 5. Droste Space Preview

**Status**: local prototype  
**Tech**: HTML, CSS, JavaScript, Canvas  
**Role**: independent prototype

This was a local preview tool before the WebGL version. It lets the user upload an image, set a transformation center, adjust parameters, and export the result.

### What It Demonstrates

- quick prototyping of an interactive visual idea
- iterative development from Canvas prototype to a cleaner public WebGL tool
- turning a one-off experiment into a more presentable project

## 6. Python GUI Process Card Generator

**Repository**: [theman6660/program](https://github.com/theman6660/program)  
**Tech**: Python, Tkinter, ttkbootstrap, Pillow  
**Role**: early GUI experiment

A small desktop GUI for assembling industrial process steps and generating a process-card image.

### What I Built

- process template loading
- manual process-step editing
- conflict-rule checking
- image generation through Pillow
- desktop UI built with Tkinter / ttkbootstrap

### What It Demonstrates

- early practice with desktop GUI development
- basic rule checking and structured data manipulation
- converting user-edited data into a generated visual artifact

## 7. Video Face Retrieval Experiment

**Repository**: [theman6660/vidio](https://github.com/theman6660/vidio)  
**Tech**: Python, PyQt5, OpenCV, TensorFlow, MTCNN, FaceNet  
**Role**: early computer vision experiment

A desktop experiment around face detection, embedding extraction, and video/photo indexing.

### What I Built

- TensorFlow / FaceNet model loading
- MTCNN face detection
- face embedding extraction and distance comparison
- PyQt5 GUI with worker threads for long-running tasks
- OpenCV-based video and image processing

### What It Demonstrates

- ability to connect ML models with a desktop workflow
- handling heavier local dependencies and background processing
- early exploration of computer vision application development

## 8. Other Repositories

| Repository | Type | Note |
| --- | --- | --- |
| [TJU-CourseSharing](https://github.com/theman6660/TJU-CourseSharing) | fork | Tianjin University course-sharing repository |
| [personal-website](https://github.com/theman6660/personal-website) | old / empty public repo | older website-related repository |
| [.deploy_git](https://github.com/theman6660/.deploy_git) | generated deployment artifact | not recommended as a main portfolio repo |
| [webcommit](https://github.com/theman6660/webcommit) | early repo | low priority for portfolio display |
| [vidio2](https://github.com/theman6660/vidio2) | early repo | low priority for portfolio display |

## Portfolio Strategy

For Agent Harness / AI engineering opportunities, I recommend reading these first:

1. Deep Reader
2. Telegram AI Bot
3. Personal Website Automation
4. Escher Droste Tool

The first three show LLM engineering, automation, context, state, deployment, and workflow thinking.  
The visual and early GUI projects show broader implementation range, but they should not be the main signal for an Agent Harness role.

## Planned Work

- publish Deep Reader as a clean public repository
- build a small Agent Harness Lab with tool registry, task loop, trace view, memory strategy switch, and failure recovery
- write technical notes about context engineering, tool-use failure modes, and agent trace design
- make each major repository easier to evaluate through README, screenshots, runnable examples, and tests
