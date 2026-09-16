<h1 align="center">Build Emma</h1>

<p align="center">
  <b>Build software with a resident agent — on your own models, on your own machine.</b>
</p>

<p align="center">
  <a href="https://buildemma.com"><b>buildemma.com</b></a> ·
  <a href="../../releases/latest"><b>⬇️ Download</b></a> ·
  <a href="MANUAL.md"><b>Manual</b></a> ·
  <a href="https://discord.gg/cJVHKNeCxP"><b>Discord</b></a> ·
  <a href="SECURITY.md"><b>Security</b></a>
</p>

---

Build Emma is a desktop app for writing code. It has everything you'd expect from an
editor you use all day — files, tabs, search, a terminal, git, a debugger, language
support — and at the heart of it is **EMMA**, an agent you can hand real work to.

She reads your project, makes the change, runs your tests, and fixes what fails. Then she
**stops and shows you the diff.** Nothing touches your code until you've read it and said yes.

`local-first · no account · no telemetry · works offline · cloud models optional`

> **This repo is just the downloads.** There's no source code here. It's where the
> installers live, and where Build Emma looks to see if there's an update.

## Download

**[Get the latest release →](../../releases/latest)**

| | |
|---|---|
| **Windows** | `Build.Emma_…_x64-setup.exe` — the installer, and the one that updates itself · or the `.msi` |
| **Linux** | `Build.Emma_…_amd64.AppImage` — portable: mark it executable and run it · or the `.deb` (Debian, Ubuntu) / `.rpm` (Fedora) |
| **macOS** | Not yet. It builds, but it hasn't had its install testing, and it won't ship untested. |

**On Windows**, the installer isn't code-signed yet, so the first time you run it Windows
says *"Windows protected your PC"*. Click **More info → Run anyway**. Unsigned means no
certificate has been bought — not that nothing was checked.

**You'll also need [Ollama](https://ollama.com), and the biggest model your computer can run.**
EMMA's work is only as good as the model doing it — a bigger model makes fewer mistakes and
handles bigger jobs.

| Graphics memory | Model |
|---|---|
| **24 GB or more** | `ollama pull qwen3-coder:30b` or `ollama pull qwen3:32b` |
| **12–16 GB** | `ollama pull qwen3:14b` |
| **6–8 GB** | `ollama pull qwen3:8b` — the smallest we'd recommend |

For the best results of all, add a Claude or OpenAI key — bring your own, and it's kept in an
encrypted vault on your machine.

## Try it, then buy it once

**Free for 30 days, with everything included.** If it earns a place on your machine, it's
**£89, once** — [buy at buildemma.com](https://buildemma.com/#buy).

- **No subscription, no account.** Your key arrives by email a minute after paying.
- **It's checked on your own computer.** Nothing phones home, and nothing stops working if
  we ever do.
- **Every 2.x update is included**, on up to two of your own computers.
- **30-day refunds**, no questions asked.

If the trial ends and you haven't bought, EMMA stops making changes — but your files, the
editor, the terminal and git all keep working, and nothing is locked or deleted.

The full terms are short and in plain English: [licence](https://buildemma.com/licence) ·
[privacy](https://buildemma.com/privacy).

## Updates

Build Emma checks this page for a newer version when it starts, tells you when there is
one, and installs it **only when you say so**. Every update is signed, and your copy refuses
one that isn't. You can turn the check off in **Settings → Updates**.

## Checking a download

Every release lists a SHA-256 checksum for each file, and includes them in `SHA256SUMS`:

```bash
sha256sum -c SHA256SUMS --ignore-missing
```

## Help

- **How do I…?** — the [manual](MANUAL.md)
- **Something's broken, or you've an idea** — [Discord](https://discord.gg/cJVHKNeCxP), or email **Gregorymoores@proton.me**
- **A security problem** — please read [SECURITY.md](SECURITY.md) first
