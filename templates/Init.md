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
<%*
const des = await tp.system.prompt("What is it about? (if there is anything that title can't say)", "");
-%>
---
tags:<% tagsYaml %>
maturity: baby
status: active
created: <% tp.date.now("YYYY-MM-DDTHH:mm:ssZ") %>
updated_count: 0
updated: <% tp.date.now("YYYY-MM-DDTHH:mm:ssZ") %>
viewed: <% tp.date.now("YYYY-MM-DDTHH:mm:ssZ") %>
description: <% des %>

---
