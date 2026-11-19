<%*
const current = tp.file.path(true);
const resolved = app.metadataCache.resolvedLinks;

// notes that link to this note (excluding itself)
const sources = Object.keys(resolved).filter(
  src => src !== current && resolved[src][current]
);

let tags = [];
if (sources.length === 1) {
  const file = app.vault.getAbstractFileByPath(sources[0]);
  const fm = app.metadataCache.getFileCache(file)?.frontmatter;
  let t = fm?.tags ?? [];
  if (typeof t === "string") t = t.split(/[,\s]+/);
  tags = t.filter(Boolean).map(x => String(x).replace(/^#/, ""));
}

const tagsYaml = tags.length ? "\n" + tags.map(t => `  - ${t}`).join("\n") : "";
-%>
---
tags:<% tagsYaml %>
maturity: baby
status: active
create at: <% tp.date.now("YYYY-MM-DDTHH:mm:ssZ") %>
last update: <% tp.date.now("YYYY-MM-DDTHH:mm:ssZ") %>
---

<%*
const des = await tp.system.prompt("What is it about? (if there is anything that title can't say)", "");
-%>
> [!note] What is it about?
> <% des %>

start writing here...