---
icon: list-checks
tags: [moc/inbox]
related: "[[structure]]"
---
# ☑️ Task summary (Tasks + Dataview)

**Test data.** A live aggregator — counts how much is open, not what
matters more ([[Focus]] is about priorities).

## Projects — open tasks (Dataview)

```dataviewjs
const QUESTION_NUMS = ["20"];
const DECISION_NUMS = ["30"];

const readmes = dv.pages('"JDPARA-EN/(P) Projects"')
	.where(p => p.file.name === "README")
	.sort(p => p.file.folder);

const folderNum = (folderPath) => folderPath.split("/").pop().split("-")[0];

const countIn = (folder, nums) => {
	const tasks = dv.pages(`"${folder}"`)
		.where(p => nums.includes(folderNum(p.file.folder)))
		.file.tasks.flat();
	return { open: tasks.filter(t => !t.completed).length, total: tasks.length };
};

const rows = readmes.map(p => {
	const folder = p.file.folder;
	const projectName = folder.split("/").pop();
	const q = countIn(folder, QUESTION_NUMS);
	const d = countIn(folder, DECISION_NUMS);
	return [
		`[[${p.file.path}|${projectName}]]`,
		`${q.open} / ${q.total}`,
		`${d.open} / ${d.total}`,
	];
});
dv.table(["Project", "Questions (open/total)", "Decisions (open/total)"], rows);
```

## Plain tasks (Tasks plugin)

```tasks
not done
path includes JDPARA-EN/(P) Projects
```
