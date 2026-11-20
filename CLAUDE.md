# Accountable Support

Accountable Support is a ticket system for the support team of the business that uses Accountable, its CRM. Customers raise tickets, and the team answers them. It is a companion app in the Accountable suite with its own repo and its own database.

## Where to find things

- `docs/intent.md`: what to build, feature by feature, with the sample customers
- `docs/TECH_STACK.md`: how to build it, with the commands and the ports
- `.claude/skills/brand/SKILL.md`: Accountable's fonts, colors and tone
- `course/`: the steps for the person following the course, not needed for building

Read the intent and the tech stack before you start, then build only the feature you were asked for. Read the brand file before you build any screen and follow it, so Support matches the rest of the Accountable suite.

## How to work

- Work on a branch of your own and open a pull request into `main`. Never push to `main` and never merge a pull request; the lead reviews and merges every pull request.
- Commit and push to your branch as you go, so nothing is lost if your session stops.
- Keep each pull request to one feature. Add tests for what you build, and make sure `npm test` passes before you open the pull request.
- Keep the "Running the app" section of `README.md` up to date with how to run the app and what it does so far. Leave the rest of `README.md` as it is.
