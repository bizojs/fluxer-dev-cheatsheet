# The Fluxer Development Cheat Sheet

A helpful guide for common development issues.

---

- [The Fluxer Development Cheat Sheet](#the-fluxer-development-cheat-sheet)
    - [error: failed to create directory `/.../target/debug`](#error-failed-to-create-directory-targetdebug)
    - [Cannot find module '@app/features/i18n/...'](#cannot-find-module-appfeaturesi18n)
    - [How do I open the dev server in my browser?](#how-do-i-open-the-dev-server-in-my-browser)
    - [How do I verify my email?](#how-do-i-verify-my-email)

---

### error: failed to create directory `/.../target/debug`
Go into `.devcontainer/devcontainer.json` and in the `postCreateCommand`, insert the following code at the beginning:
```sh
sudo chown -R vscode:vscode /workspaces/fluxer/target &&
```

so the `postCreateCommand` looks like this:

```json
"postCreateCommand": "sudo chown -R vscode:vscode /workspaces/fluxer/target && find /workspaces/fluxer -maxdepth 4 ...",
```

---

### Cannot find module '@app/features/i18n/...'
You will need to run the `i18n:compile` script to generate the necessary language keys.

```sh
pnpm i18n:compile
```

If this doesn't work, make sure you have installed all the necessary packages with `pnpm i`

---

### How do I open the dev server in my browser?
In the website address bar, type `http://localhost:8088` and hit enter, or simply click [here](http://localhost:8088)

---

### How do I verify my email?
When you register an account on the dev server, you may be asked to verify your email. This email will be put in the mailpit instead of actually sent via a mail server.

The mailpit can be found at `http://localhost:8088/devmail`
