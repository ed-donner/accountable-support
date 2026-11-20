# Week 2 Day 4: the optional Claude Code Projects lesson

My steps for building Accountable Support with Claude Code Projects. Accountable Support is a ticket system for the support team behind Accountable.

In a project, Claude acts as a coordinator. It hands each piece of work to a thread. A thread is a separate Claude Code session that runs in the cloud on its own branch.

This repo starts with:

- `docs/intent.md`: the six features to build and the sample customers
- `docs/TECH_STACK.md`: the stack, the commands and the ports
- `CLAUDE.md`: instructions for the agents
- `.claude/skills/brand/SKILL.md`: Accountable's brand skill, so Support matches the rest of the suite

## Before you start

- Claude Pro or higher (https://claude.com/pricing). Projects are in beta and aren't on every account yet, or on Team and Enterprise plans. To check, open the Code tab in the Claude desktop app, or https://claude.ai/code, and look for Projects in the sidebar or under More.
- A GitHub account
- Node.js 24 or later and uv, as for Accountable
- About two hours. Most of it is the agents working.

Projects are part of Claude Code. If you use a different coding agent, I suggest watching this lesson rather than following along.

## 1. Make your own copy of this repo

On this repo's GitHub page, click **Use this template**, then **Create a new repository**. Choose your own account as the owner and name it `accountable-support`. It can be private or public.

Use the template rather than a fork. With a fork, the agents' pull requests could go to my repo instead of yours.

## 2. Give Claude access to your copy

The threads use the Claude GitHub App to push their branches and open pull requests. If you haven't installed it, install it from https://github.com/apps/claude and choose your new repo. If you installed it for selected repositories only, add your new repo at https://github.com/settings/installations.

## 3. Create the project

Open Projects and create a project called Accountable Support. Add your new repo to it, then open the project's settings:

- **General:** choose Sonnet 5.5 at medium effort for both the coordinator and the threads.
- **Memory:** paste these instructions:

```
We're building Accountable Support from docs/intent.md, using the tech stack in docs/TECH_STACK.md.

Start with feature 1, the foundation, as one thread with one pull request. When I've merged it, start features 2 to 6 at the same time, with a thread and a pull request for each.

I'll review and merge every pull request. Only post an update when a pull request is ready for me or a thread is stuck.
```

- **Environment:** the cloud comes with Node 22. Add this setup script to install Node 26:

```
#!/bin/bash
set -e
npm install -g n
n 26
```

## 4. Start the build

Send the project this message:

```
Build Accountable Support from docs/intent.md.
```

## 5. Review and merge the foundation

The coordinator starts a thread to build the foundation. When the thread is done, it opens a pull request. Open it on GitHub, check that CI passed and look through the changes. Then merge it.

## 6. Review and merge the other five features

The coordinator then starts five threads, one for each of features 2 to 6. They all work at the same time. Each thread opens its own pull request. If CI fails, the thread fixes the problem and pushes again.

Merge the pull requests one at a time. After a merge, another pull request may show a conflict. Its thread doesn't find out by itself, so ask the project to update that pull request from `main`.

## 7. Run it on your computer

Clone your repo into your projects folder, beside `accountable`. Use your own GitHub name in the address:

```
git clone https://github.com/YOUR-GITHUB-NAME/accountable-support.git
cd accountable-support
npm run dev
```

Then open http://localhost:5180.
