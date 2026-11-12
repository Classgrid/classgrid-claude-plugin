# Classgrid for Claude

The official [Classgrid](https://classgrid.in) plugin for Claude. It connects Claude to your own Classgrid account,
so you can ask Claude about your Classgrid projects and their code, find things in your past Classgrid AI chats,
read and write your live docs, publish pages, manage your schedules and reminders, catch up on your Grid team chats,
and use the apps you have connected to Classgrid.

## Install

In Claude Code:

```
/plugin marketplace add Classgrid/classgrid-claude-plugin
/plugin install classgrid@classgrid
```

The first time Claude uses a Classgrid tool, a Classgrid sign-in page opens in your browser, followed by the
Classgrid permission screen. You choose exactly what Claude may access there.

## What it can do

| Permission on the Classgrid screen | Starts | What Claude can do |
|---|---|---|
| Read your profile | always on | Look up your name, email and role |
| Read your projects and their code on GitHub | ticked | List your projects (Project Mode and Mastero), see their details, list, read and search the code in each project's GitHub repo |
| Read your Classgrid AI chat history | **unticked** | List, search and read your past Classgrid AI chats (never incognito chats) |
| Read your Classgrid AI skills and memory | **unticked** | Read the skills and preferences you saved in Classgrid AI |
| Read your live docs | ticked | List and read your live docs |
| Create and edit your live docs | unticked | Create docs, edit them and answer comments |
| Publish pages and answer their comments | unticked | Publish a page at chat.classgrid.in/p/… and manage its comments |
| Read your schedules | ticked | See your schedules and reminders |
| Create, edit and delete your schedules | unticked | Make and change schedules and WhatsApp/email reminders |
| Read your Grid chats and groups | ticked | Read the Grid chats, groups, members and polls you belong to |
| Send messages in Grid and chats | unticked | Send messages, polls, announcements and files as you |
| Use your connected apps | unticked | Use apps you already connected to Classgrid (Gmail and Google Workspace, Microsoft 365, Notion, Slack, Canva, Spotify, GitHub, Zoom, YouTube) |
| Stay connected | ticked | Keep you signed in without asking again |

Anything that reads private history or can change something is off until you tick it.

## Skills

- `classgrid-setup`: connecting your account and what the plugin can do
- `classgrid-projects`: your projects and their code on GitHub
- `classgrid-chat-history`: your past Classgrid AI chats (only if you allowed it)
- `classgrid-memory`: your Classgrid AI skills and memory (only if you allowed it)
- `classgrid-docs`: live docs and their comments
- `classgrid-pages`: publishing pages
- `classgrid-schedules`: schedules and reminders
- `classgrid-grid`: Grid team chats and groups
- `classgrid-apps`: your connected apps

## What this plugin runs, sends and fetches

- **Runs:** nothing on your computer. The plugin has no scripts, no commands and no hooks. It is the skill files
  above and one MCP server address.
- **Connects to:** the Classgrid MCP server at `https://api.classgrid.in/mcp` (remote, over HTTPS). Sign-in uses
  OAuth 2.1 with PKCE through `https://api.classgrid.in`; Claude keeps the access token, and no password or key is
  stored in this plugin.
- **Sends:** the tool calls Claude makes (for example a project id and a file path, a search phrase, or a message
  you asked Claude to send), with your Classgrid access token.
- **Fetches:** only data from your own Classgrid account that the permissions you ticked allow. Project code is read
  by the Classgrid server from the project's GitHub repo (default branch) using the GitHub access you gave
  Classgrid; Claude never gets a GitHub key. Secret files (.env, keys, certificates) are never sent, and secret
  values in code are replaced with `[hidden secret]`. Connected apps are reached by the Classgrid server with the
  access you gave Classgrid.

## Privacy and control

- Every tool acts as you and only on your own data: your projects, chats, docs, pages, schedules and the Grid chats
  you are a member of.
- You can remove Claude's access at any time in Classgrid under **AI Plugins > Connected apps**.
- Privacy policy: https://classgrid.in/privacy
- Terms: https://classgrid.in/terms

## Support

Email support@classgrid.in or visit https://classgrid.in.
