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

On this repo's GitHub page, click **Use this template**, then **Create a new repository**. Choose your own account as the owner and give it any name you like, such as `accountable-support`. It can be private or public.

Use the template rather than a fork. With a fork, the agents' pull requests could go to my repo instead of yours.

## 2. Give Claude access to your copy

The threads use the Claude GitHub App to push their branches and open pull requests. If you haven't installed it, install it from https://github.com/apps/claude and choose your new repo. If you installed it for selected repositories only, add your new repo at https://github.com/settings/installations.

## 3. Create the project

Open **Projects** in the sidebar and click **New project**. Name it Accountable Support and leave "What do you want to work on?" empty. Under **Context**, click **+**, choose **Add repository** and pick your new repo. Make sure **Project coordinator** is on, then click **Create project**.

When the project opens, the coordinator looks through the repo and may suggest some threads. Leave those and open the project's settings.

In **General**, choose Sonnet 5.5 for the coordinator, and Sonnet 5.5 at medium effort for the threads. If it asks about existing threads, update them to Sonnet 5.5 as well.

Then open **Memory**, paste these into **Project instructions** and click **Save changes**:

```
We're building Accountable Support from docs/intent.md, using the tech stack in docs/TECH_STACK.md.

Start with feature 1, the foundation, as one thread with one pull request. When I've merged it, start features 2 to 6 at the same time, with a thread and a pull request for each.

I'll review and merge every pull request. Each time I merge one, update the other open pull requests from main. Once ticket detail (feature 2) is merged, add each feature to the ticket page where the intent asks for it.

Only post an update when a pull request is ready for me or a thread is stuck.
```

## 4. Review and merge the foundation

As soon as you save the instructions, the coordinator starts a thread to build the foundation. You don't need to send it a message. After a few minutes the thread opens a pull request. Open it on GitHub, check that CI passed and look through the changes. Then merge it.

## 5. Review and merge the other five features

When you merge the foundation, the coordinator starts five threads, one for each of features 2 to 6. They all work at the same time. Each thread opens its own pull request. If CI fails, the thread fixes the problem and pushes again.

Merge ticket detail (feature 2) first. The SLA times, the knowledge base articles and the customer ratings all show on its page.

After that merge, the other pull requests may have merge conflicts. Their threads don't find out by themselves, so tell the coordinator. With your own pull request numbers, I sent:

```
After merging PR 6, I notice PR 2 has merge conflicts, as others might do. Please resolve merge conflicts. Please always do this after I merge each PR.
```

Then merge the others one at a time. After each merge, the coordinator has the threads update the other pull requests from `main`. Wait until a pull request is ready to merge and its CI has passed before you merge it.

## 6. Run it on your computer

Clone your repo into your projects folder, beside `accountable`. Use your own GitHub name, and your repo's name if it isn't `accountable-support`:

```
git clone https://github.com/YOUR-GITHUB-NAME/accountable-support.git
cd accountable-support
npm run dev
```

Then open http://localhost:5180.
