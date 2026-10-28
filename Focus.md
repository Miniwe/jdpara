---
icon: target
tags: [moc/inbox]
related: "[[Task summary]]"
---
# 🎯 Focus

**Test data.** A live aggregator — stores nothing itself. Answers "what's
being worked on right now and what matters most there," not "how much is
open in total" ([[Task summary]] is about counts, this file is about
priorities).

The source of focus is the `priority` field in the frontmatter of each
project's `README.md`: `1` = in focus, `2` = relevant but not now, `3` =
background.

## Projects in focus (priority 1)

Rule of thumb: keep 2–4 projects at a time.

```dataviewjs
const projects = dv.pages('"JDPARA-EN/(P) Projects"')
	.where(p => p.file.name === "README" && p.priority !== undefined)
	.where(p => p.priority === 1)
	.sort(p => p.file.folder);

const count = projects.length;
if (count < 2) {
	dv.paragraph(`🟡 **${count} project(s) in focus** — below the lower bound (2).`);
} else if (count > 4) {
	dv.paragraph(`🔴 **${count} projects in focus** — above the upper bound (4).`);
} else {
	dv.paragraph(`🟢 **${count} project(s) in focus** — within the normal range (2–4).`);
}

if (count > 0) {
	dv.table(
		["Project", "Status", "Updated"],
		projects.map(p => [
			`[[${p.file.path}|${p.file.folder.split("/").pop()}]]`,
			p.status ?? "—",
			p.updated ?? "—",
		])
	);
}
```

## Open questions in focus projects — by priority

```dataviewjs
const RANK = { "blocker": 0, "high": 1, "normal": 2, "someday": 3 };

const focusProjects = dv.pages('"JDPARA-EN/(P) Projects"')
	.where(p => p.file.name === "README" && p.priority === 1)
	.sort(p => p.file.folder);

if (focusProjects.length === 0) {
	dv.paragraph("No projects with `priority: 1` — the question list isn't built.");
} else {
	for (const proj of focusProjects) {
		const folder = proj.file.folder;
		const projectName = folder.split("/").pop();

		const questions = dv.pages(`"${folder}/20-questions"`)
			.where(p => p.file.name.startsWith("Q-"))
			.where(p => p.status === "open");

		dv.header(4, projectName);
		if (questions.length === 0) {
			dv.paragraph("_no open questions (or the project doesn't keep a `20-questions` folder)_");
		} else {
			const rows = questions
				.sort(p => RANK[p.priority] ?? 2)
				.map(p => [`[[${p.file.path}|${p.id}]]`, p.priority ?? "—", p.status ?? "—"]);
			dv.table(["Question", "Priority", "Status"], rows);
		}
	}
}
```

## How to change focus

1. Open the relevant project's `README.md`, adjust `priority:` (1/2/3).
2. A specific question's priority — edit the `priority` field in the
   `20-questions/Q-….md` card itself.
