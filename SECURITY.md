# Security

Build Emma runs on your machine, holds your code and your API keys, and can run commands
when you let it. So a security report isn't a nuisance — it's someone helping keep the
promise the whole thing rests on. Reports are welcome, credited if you'd like, and answered
by a person.

## Reporting a problem

**Email `Gregorymoores@proton.me`.**

Please don't post a security bug in Discord or anywhere public, and please give me a chance
to fix it before you talk about it. If you'd rather encrypt it, send a first email with no
details and I'll reply with a key.

What helps most, roughly in order:

- **What someone could do with it**, and what they'd need first — another program on the
  same computer? A project folder they send you? Someone on your network? A web page you visit?
- **Your version** — shown in the status bar at the bottom of the window.
- **Your system and how you installed it** — Windows installer, `.msi`, AppImage, `.deb`, `.rpm`.
- **How to make it happen.** A rough sketch is fine; a vague real problem beats no report.

## What to expect

| | |
|---|---|
| **A reply** | within a few days |
| **A fix** | as fast as the problem deserves — serious ones go out as an update straight away |
| **Credit** | in the release notes, if you want it |

## Which versions get fixes

| Version | |
|---|---|
| **2.x** | ✅ Fixed, and delivered as an in-app update |
| Anything older | Wasn't publicly released |

## What's already in place

So you know what you'd be testing against:

- **The app only listens on your own computer.** Its internal connection needs a secret that
  changes every launch, and web pages you visit can't reach it.
- **API keys can be locked** behind a passphrase you choose, encrypted on disk, and never sent
  to us.
- **EMMA asks before running any command**, and every change she makes waits for your approval
  — except the night shift, which you schedule on purpose, snapshots your project first, and
  never runs commands.
- **A project you download can't reach outside its own folder** through links, and can't
  schedule EMMA to work unattended.
- **Sharing a session** needs a join code, the host's approval, and a limit on wrong guesses.
  A peer can't reach your shell unless you turn that on, and then a second switch for typing.
- **Updates are signed**, and a tampered download is refused before anything is written.
- **Nothing phones home.** No telemetry, no analytics, and crash reports stay on your machine
  unless you set somewhere to send them.

## What's out of scope

- Anything that needs someone to already control your user account — at that point they have
  your files anyway.
- Plugins you chose to install. They run sandboxed, but only install ones you trust.
- Cloud models you connect: what you send them is governed by that provider.
