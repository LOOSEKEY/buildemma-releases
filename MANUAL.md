<h1 align="center">Manual</h1>

<p align="center">
  <i>How to use Build Emma, from installing it to handing EMMA a night's work.</i>
</p>

<p align="center">
  <a href="README.md"><b>← Back</b></a> ·
  <a href="https://buildemma.com"><b>buildemma.com</b></a> ·
  <a href="../../releases/latest"><b>⬇️ Download</b></a> ·
  <a href="https://discord.gg/cJVHKNeCxP"><b>Discord</b></a>
</p>

---

**Hover over any button** and it tells you what it does. Almost everything is also in the
**command palette** — press **`Ctrl+Shift+P`** and start typing.

- [Getting started](#getting-started)
- [The editor](#the-editor)
- [EMMA](#emma)
- [Models and chat](#models-and-chat)
- [Voice](#voice)
- [Building together](#building-together)
- [Safety nets](#safety-nets)
- [Adding tools and plugins](#adding-tools-and-plugins)
- [Settings](#settings)
- [Your licence](#your-licence)
- [Updates and crash reports](#updates-and-crash-reports)
- [Where your files live](#where-your-files-live)
- [If something's wrong](#if-somethings-wrong)

---

## Getting started

**1. Install Ollama** from [ollama.com](https://ollama.com), then get **the biggest model your
computer can run.** EMMA's work is only as good as the model doing it: a bigger model makes
fewer mistakes, needs fewer tries, and copes with bigger tasks. Choose by how much memory
your graphics card has:

| Graphics memory | Model |
|---|---|
| **24 GB or more** | `ollama pull qwen3-coder:30b` or `ollama pull qwen3:32b` |
| **12–16 GB** | `ollama pull qwen3:14b` |
| **6–8 GB** | `ollama pull qwen3:8b` — the smallest we'd recommend |

For the best results of all, add a **Claude or OpenAI key** in the Models panel.

Two more are worth having:

```bash
ollama pull qwen2.5-coder     # for completions as you type, and code questions
ollama pull nomic-embed-text  # for searching your project by meaning
```

**What makes a good model for EMMA** is how reliably it uses tools — reading files, editing
them, running tests — and size decides that more than anything, including "coder" in the
name. A small model will still work, but it takes more tries, and you'll reject more of its
changes in review.

**2. Install Build Emma** from the [latest release](../../releases/latest):

- **Windows:** the `-setup.exe`. The first time, Windows says *"Windows protected your PC"* —
  click **More info → Run anyway**. (It isn't code-signed yet.)
- **Linux:** the `.AppImage` — right-click → Properties → allow executing, or
  `chmod +x` it — then run it. Or install the `.deb` / `.rpm`.

Everything else is inside: the editor, EMMA's engine, and language support for
TypeScript, JavaScript and Python.

**3. Open it.** You start in a `BuildEmma` folder in your home directory. To work on a real
project, use **Workspace: Open Folder…** in the command palette, or the folder button in the
Explorer.

While it starts you'll see a quiet room — a lamp, an armchair, a coffee going cold. That's
also what an empty editor looks like. If motion is turned off on your system, the lamp is
simply already on.

## The editor

Down the left side: **Explorer**, **Search**, **Project map**, **Tests**, **Source Control**
and **Models**.

| Keys | |
|---|---|
| `Ctrl+P` | Open a file by typing part of its name |
| `Ctrl+Shift+P` | Command palette |
| `Ctrl+S` | Save |
| ``Ctrl+` `` | Show or hide the terminal |
| `Ctrl+\` | Split the editor |
| `F12` / `Ctrl+click` | Go to definition |
| `F2` | Rename everywhere it's used |
| `Ctrl+.` | Quick fixes and refactorings |
| `Ctrl+,` | Settings |

**Languages.** TypeScript, JavaScript and Python work straight away — errors underlined as you
type, hover for details. Rust, Go, C/C++, C#, Java, PHP, Ruby, Zig and Lua work too once their
language server is installed; **Settings** lists each one and the command that installs it.

**Search** finds text across the project. Its **Semantic search** toggle finds code by what it
*means* — build the index once from there (it needs `nomic-embed-text`).

**Project map** shows which files the rest of the project depends on most, so you can see
where the important code is.

**Source Control** shows your changes, lets you stage and commit, and can draft the commit
message from what you've staged.

**Debugging.** Click beside a line number to set a breakpoint, then `F5`. While paused you get
the call stack, variables and a watch list. `F10` step over, `F11` step into, `Shift+F11` step
out, `Shift+F5` stop. If your language's debugger isn't installed, Build Emma tells you the
command to install it.

**Tests.** The Tests panel finds your tests by reading your code, before you've run anything.
Run one, a file, or all; failures link to the line. A hollow dot means *not run yet*.

**Merge conflicts** open in a merge editor with the choices above the file, named after your
actual branches.

**Notebooks** (`.ipynb`) open as cells you can run. Anything in the file Build Emma doesn't
understand is kept exactly as it was when you save. Plots and images aren't shown yet; text
output is.

**More than one folder:** **Workspace: Add Folder to Workspace…** — for a service and its
client side by side.

**Another machine:** **Workspace: Connect to a Remote Machine…** runs Build Emma's engine
*on* that machine over SSH, so saving and searching are fast however far away it is. This is
the newest part of the app — if it gives you trouble, please say so on Discord.

**Live preview** for web projects: **View: Toggle Live Preview**, then enter your dev
server's address.

## EMMA

Open the **EMMA** tab and describe what you want done.

She works through it step by step — reading files, searching the project, making changes,
and **asking before she runs any command**. When she's finished you get a **diff**: every
change, file by file, and you can untick any part you don't want. **Nothing is written until
you approve it.**

**She checks her own work.** If your project has tests (or a type-check, lint or build), she
runs them against her changes before showing you, and fixes what fails. The badge on the diff
tells you whether they pass. If she was asked for a change and made none, her summary says
**No files were changed** first, so a confident-sounding reply can't hide an empty diff.

The buttons by the message box:

| | |
|---|---|
| **Queue** | Line up several tasks. She does them one at a time and waits for your approval between each, so later tasks build on what you accepted. |
| **Assembly line** | Splits a bigger task into parts that run at the same time where they can, then a reviewer checks the combined result and fixes what it finds. |
| **Crew** | EMMA hands pieces of work to named teammates — Ada, Grace, Hedy and others, each with a specialty — and you watch each one think. Name another project folder in your request and a teammate can work there. |
| **Night shift** | Each line in the box is a task, run while you're away. It snapshots your project first, applies changes without asking, and **never runs commands**. Set a time to make it nightly. |
| **Mentor mode** | She explains her reasoning as she goes. |
| **Where were we?** | A recap of the project from her notes and recent work. |

**The night shift applies changes without review**, so give it your strongest model, and read
the morning's results before building on them. Undo is **Time Machine: Restore Checkpoint…**.
A schedule only runs if you set it in Build Emma on this computer — if one arrives inside a
project you downloaded, it waits for you to review and allow it.

**What she remembers about your project:**

- **EMMA: Project Notes** — what she's learned about the project. She reads it before every
  task and adds to it. You can edit it.
- **EMMA: Standing Orders** — your rules for every task: *"always add tests"*,
  *"no new dependencies"*.

Teammates on the crew keep their own notes too, and you can read and correct them.

**Starting from scratch:** **Factory: New Project from Spec…** — describe what you want, and
EMMA sets up a working project for you to review.

**Which model does she use?** The one in the model picker — a local model, or Claude or GPT if
you've added a key. Pick per task.

## Models and chat

The **Models** panel lists your Ollama models, pulls new ones with a progress bar, and deletes
old ones. **Benchmark speed** measures how fast a model really runs on your machine, and
EMMA uses that when choosing.

**Cloud models:** add a Claude or OpenAI key in the Models panel. Cloud is always your pick —
automatic routing stays local.

**Protect your keys:** the lock button in the title bar sets a passphrase. Your keys are then
encrypted on disk and the app asks for the passphrase when it opens. It's optional. The
passphrase is never stored and never leaves your computer — if you forget it, you re-enter
your keys. Your system can remember it for you (**Settings → Security**), which is convenient
but means anyone using your logged-in computer can open Build Emma.

**Chat** talks to whichever model you choose. **Auto** picks the best one for each message.
You can attach the open file or your selection, and when you're working with others you can
chat privately or with the whole session.

**Completions as you type** ("ghost text") come from a local model — turn them on in the status
bar. A code model works best.

## Voice

Voice runs entirely on your computer — no audio goes anywhere. It needs a one-time setup
because the speech models are large:

```bash
python3 -m venv ~/.config/buildemma/voice-venv
~/.config/buildemma/voice-venv/bin/pip install faster-whisper piper-tts
```

Then download a voice from the [Piper voices](https://huggingface.co/rhasspy/piper-voices)
collection and put `en_US-amy-medium.onnx` and its `.onnx.json` in `~/.config/buildemma/voices/`.

After that you can hold to record a message, have EMMA's replies read aloud, and turn on
**"Hey EMMA"** — which listens locally and ignores near-misses like *"dilemma"*.

## Building together

**Session: Host / Join (LAN)…**

**Hosting** gives you a six-digit code. People on your network see your session in their
**Join** tab (the code itself is never broadcast). Each person who joins waits for you to let
them in as an **editor** or a **viewer**, and you can change that or remove them any time.
Five wrong codes from one device, or twenty from anywhere, and joining pauses — start hosting
again for a new code.

**Together you get** live editing with everyone's cursor in their own colour, a shared EMMA
conversation, and push-to-talk voice. Viewers can talk and chat but not edit. Click someone in
the status bar to **follow** them as they move around the code.

**Identities are verified.** Each person has a key that proves they are who they say, shown
as a fingerprint. **Trust** someone once and they're let straight in next time.

**Pool your graphics cards.** Everyone's models appear in the picker, so a light laptop can use
the room's biggest GPU — for chat, EMMA and the crew. The fleet view shows every machine, what
it can run and how busy it is, and work goes to the one that'll finish soonest. Your files stay
on your machine.

**Sharing your terminal** is off until you turn it on, and letting someone *type* in it is a
second, separate switch. Neither is remembered after the session.

**Over the internet:** an optional tunnel through a server you already have. It asks twice
before opening, and won't open while anyone's join is still waiting for approval.

## Safety nets

- **Time Machine: Save Checkpoint** snapshots the whole project; **Restore Checkpoint…** shows
  exactly what would change before it rolls back. The night shift saves one automatically.
- **Session: Replay / History…** — every task EMMA ran and every checkpoint, with one-click
  restore.
- **Workspace: Export Project** packs your project and EMMA's notes into one file.

## Adding tools and plugins

**MCP servers** add tools EMMA can use — there are one-click options for files, git, fetching
pages and memory in the Models panel.

**Plugins** add commands and EMMA tools. Put them in `.buildemma/plugins/` (one project) or
`~/.config/buildemma/plugins/` (every project), or install from a file, folder or git repo in
the **Plugins** section of the Models panel, which shows what each one can and can't do
before you install it. They run
sandboxed — **but only install plugins you trust.** **Plugins: Reload** picks up changes.

## Settings

**`Ctrl+,`**. The **You / This project** switch decides where a change is saved: *You* applies
to everything on this computer; *This project* travels with the project, for things like tab
size that a team should share. Some settings — your shell, fonts and theme — can only be yours.

**Themes:** eight built in, a colour picker that builds a whole theme from one colour and
checks it stays readable, and VS Code theme import.

**Keybindings** are the last section: click a shortcut and press the keys you want.

## Your licence

Build Emma is **free for 30 days** from the first time you open it, with everything working.
**Settings → Licence** shows how many days are left, and in the last week a reminder appears at
the top of the window (**Later** hides it).

When the trial ends without a key, **EMMA stops making changes** — her tasks, the crew, the
assembly line and the night shift. Your files, the editor, the terminal, git and chat all keep
working. Nothing is locked or deleted.

**Buying:** **£89, once**, at [buildemma.com](https://buildemma.com/#buy). Your key arrives by
email about a minute later. Paste it into **Settings → Licence** and press **Activate** — it
doesn't matter if the email split it across lines. It's checked on your computer, with no
internet needed, and covers up to two of your own computers.

Every 2.x update is included, and you can have a refund within 30 days — see the
[licence](https://buildemma.com/licence). **Lost your key?** Email Gregorymoores@proton.me from
the address you bought with.

## Updates and crash reports

When Build Emma starts it checks for a new version and, if there is one, shows a bar at the
top of the window with the release notes. **It never installs anything by itself.** Every
update is signed, and a tampered one is refused. Turn the check off in **Settings → Updates**,
or check any time with **Help: Check for Updates**. Being offline is fine.

**If it crashes,** a report is saved on your computer and shown next time you open the app —
with your API keys and home folder already removed, so what you see is exactly what's in the
file. **Nothing is sent anywhere** unless you set a destination yourself in
**Settings → Crash reports**.

## Where your files live

**In each project,** a `.buildemma` folder holds EMMA's notes, your standing orders, a record
of her tasks, the search index, checkpoints and project plugins. Commit it or ignore it —
your choice. Delete it and your code is untouched.

**On your computer,** `~/.config/buildemma/` holds your settings, your keys (encrypted if you
set a passphrase), trusted collaborators, your trial date and licence key, and the voice setup.

## If something's wrong

**It says the engine didn't start.** On a slow first launch it can take a while — Build Emma
waits up to two minutes on its own. If it still fails, the reason is in `launch.log`, which is
worth attaching to any report:

| | |
|---|---|
| **Windows** | `%LOCALAPPDATA%\dev.loosekey.buildemma\logs\launch.log` |
| **Linux** | `~/.local/share/dev.loosekey.buildemma/logs/launch.log` |

**No models in the picker** — Ollama isn't running, or has no models. Try `ollama list`.

**No errors underlined for Rust, Go and others** — install that language's server (Settings
lists the command), then reopen the file.

**Semantic search finds nothing** — pull `nomic-embed-text`, then build the index from the
Search panel.

**Voice buttons do nothing** — the voice setup or the voice file is missing; see [Voice](#voice).

**A cloud model fails straight away** — the key is missing, or your keys are locked. Add it in
Models, or unlock.

**People can't find your session** — some networks (guest Wi-Fi especially) block discovery.
Enter the host's address by hand; if that fails too, check the firewall.

**The night shift didn't run** — it only runs while Build Emma is open, unless you turn on the
system schedule, which also needs the computer awake and Ollama running. If it says *won't
run*, press **review and allow**.

**Anything else** — ask on [Discord](https://discord.gg/cJVHKNeCxP), or email
Gregorymoores@proton.me.
