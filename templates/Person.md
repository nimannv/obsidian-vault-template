---
tags:
---
# <% tp.file.title.replace(/^@/, "") %>

## 📇 Contact

---
## 📝 Notes


<%*
if (tp.file.title.startsWith("@")) {
    await tp.file.move("people/" + tp.file.title);
}
%>