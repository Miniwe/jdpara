---
type: readme
tags: [example]
---

# copilot

The **Copilot** plugin's own folder: conversation history
(`copilot-conversations`), custom prompts (`copilot-custom-prompts`),
system prompts, and the assistant's memory. Filled in by the plugin
itself — nothing gets written here by hand, except possibly custom
prompts.

Important for indexing: Copilot has a `qaExclusions` setting, and this
same folder's path should be added to it (in a real vault — `copilot`),
so the plugin doesn't index its own history as vault content when
building context for answers. Details — section 8 in
[[03 Obsidian setup|03 Obsidian setup]].
