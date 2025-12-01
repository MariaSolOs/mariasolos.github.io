+++
date = '2025-11-30T18:15:01-08:00'
title = 'My reviewing criteria'
description = 'What do I look for when reviewing Neovim PRs?'
+++

I like to review pull requests. Maybe it's a habit that stuck with me after being a computer science TA during most of my undergrad, but I just enjoy reading code. You learn a lot doing that.

I also like [LSP](https://microsoft.github.io/language-server-protocol/). I've both contributed to the protocol as part of my day job but also during the free time I spend on open source, and [although there are a lot of things wrong with the spec](https://youtu.be/JjWNw7aOAYU?si=KJskLcMAs-iPt5rk) I still find the interaction between editors and language servers fascinating.

Because of these 2 interests you can find me reviewing a lot of LSP PRs in Neovim (although sometimes I venture into some Treesitter gardening). In addition to the obvious reviewing standards (e.g. sensible variable names, adding unit tests when implementing a new feature, etc) that most projects have, I do have some specific criteria for what changes I'm willing to merge into core.

_DISCLAIMER: These are my personal guidelines, and do not reflect the official standards of the core Neovim team. Other maintainers may have different criteria._

1. **Does this fix/feature follow the spec?** LSP is nice in theory, but it's quite ambiguous and incomplete in practice. Because of this you'll find plenty of misbehaving servers, and depending on their popularity VS Code might have implemented out-of-spec workarounds on the client side. I've said this before and I'll say it again: Neovim follows the spec, we don't copy-paste VS Code hacks. So every time I review a PR that adds a new feature or fixes a bug I always check the spec to see if the change needs to be done in Neovim, and it's not just putting a bandaid on a disobedient server.

1. **Is this a change that addresses the vanilla Neovim user?** We all know that Neovim is the addictive text editor that can be customized into anyone's dream PDE. However, features in core should build upon the best default experience, and not include niche use-cases that live in a couple of dotfile repos.

1. **Is the proposed API flexible enough for customization?** As new LSP features become more widely used people will want to customize them. Making sure that additions to the API include flexible options (like custom format functions to new highlight groups) is quite important, as well as an easy way to disable/opt-out of new functionality.

1. **Docs? Tests?** Yeah these are obvious, but with the super nice testing setup that Neovim has adding new unit tests is relative straightforward, and documenting new features is a must as it allows us to rightfully tell people to RTFM.

1. **If this contributor disappears after this PR, will we be able to maintain this code?** In open source you never know when a contributor will stop being active. Because of this I review code with maintainability in mind. Can I understand the main logic behind this code? How well does it fit with the rest of the codebase? Is there enough Github context (PR description, issue links, bikesheds, etc) to understand why this change was made?

Those are the main points I can think about for now, so let me conclude here (I also like prime numbers and 5 feels like a good list length). Hopefully knowing a bit more about my reviewing criteria will encourage you to contribute to Neovim ;)
