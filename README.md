# Acupuncture

In the agent era, do you put enough care on **yourself**, the human being?

Acupuncture is designed to help humans dig into their pain points and try to eliminate the root cause, with the assistance from your familiar agent.

## Warning

The process may cause emotional discomfort, please evaluate your mental state before starting.

Keep aware of yourself when proceeding.
You may stop at any time.

## Installation

```bash
# global
npx skills add OneMoreSecond/Acupuncture

# local
cp -r ./agents/skills/acupuncture $YOUR_DESTINATION_PATH
```

## Usage

Without additional instruction, `/acupuncture` command will start with common topics or review previous topics.

You may specify a topic by putting context after the command, e.g. `/acupuncture Let's talk about stress`.

## Persistency

By default, Acupuncture will store the conversation history in `$HOME/.acupuncture` directory.
You can change the path by setting the `ACUPUNCTURE_HOME` environment variable.
