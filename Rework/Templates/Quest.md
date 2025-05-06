---
type: quest
status: "<% await tp.system.prompt("Status", "Active") %>"  
completed: false  
priority: "<% await tp.system.prompt("Priority", "Medium") %>"
given_by: "<% await tp.system.prompt("Given By", "") %>"
location: "<% await tp.system.prompt("Location", "") %>"
started_date: "<% tp.date.now("YYYY-MM-DD") %>"
completed_date: ""
tags:
  - quest
  - "<% await tp.system.prompt("Additional Tags", "") %>"
---

# <% await tp.system.prompt("Quest Name", "") %>

## Description  
<% await tp.system.prompt("Quest Description", "") %>

## Current Status  
**Status:** <% await tp.system.prompt("Status", "Active") %>  
**Priority:** <% await tp.system.prompt("Priority", "Medium") %>  
**Started:** <% tp.date.now("YYYY-MM-DD") %>  
**Completed:** <!-- Will be filled in when completed -->

## Objectives
- [ ] <% await tp.system.prompt("First Objective", "") %>
<% if ((await tp.system.prompt("Add another objective?", "yes/no")) === "yes") { %>
- [ ] <% await tp.system.prompt("Next Objective", "") %>
<% } %>
<% if ((await tp.system.prompt("Add another objective?", "yes/no")) === "yes") { %>
- [ ] <% await tp.system.prompt("Next Objective", "") %>
<% } %>

## Progress Notes
- **<% tp.date.now("YYYY-MM-DD") %>:** <% await tp.system.prompt("Initial Note", "") %>
<!-- Add new entries at the top with date for easy tracking -->

## Rewards
- **Expected:** <% await tp.system.prompt("Expected Rewards", "") %>
- **Received:** <!-- Will be filled in when completed -->

## Connections
### Related NPCs
- **<% await tp.system.prompt("Given By", "") %>:** Quest giver
<% if ((await tp.system.prompt("Add related NPC?", "yes/no")) === "yes") { %>
- <% await tp.system.prompt("Related NPC", "") %>
<% } %>

### Locations
- **<% await tp.system.prompt("Location", "") %>:** Where quest was received
<% if ((await tp.system.prompt("Add related location?", "yes/no")) === "yes") { %>
- <% await tp.system.prompt("Related Location", "") %>
<% } %>

### Related Threads
<% if ((await tp.system.prompt("Add related thread?", "yes/no")) === "yes") { %>
- <% await tp.system.prompt("Related Thread", "") %>
<% } %>

## Party Notes
<!-- Use this section for party discussions, theories, and plans regarding this quest -->