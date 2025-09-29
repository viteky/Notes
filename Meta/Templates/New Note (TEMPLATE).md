---
title: "<% tp.file.title %>"
date: <% tp.date.now("YYYY-MM-DD") %>
tags: []
---
<%*
const folders = [
  "Map Of Content",
  "Projects",
  "Resources",
  "Literature",
  "Fleeting",
  "Permanent",
  "Areas"
];
const folder = await tp.system.suggester(folders, folders);
await tp.file.move(folder + "/" + tp.file.title);
%>
# <% tp.file.title %>


