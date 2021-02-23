# Questionnaire Plugins Packager

Backend packager for questionnaire plugins.

# Internal Workings

- Requires a custom ME/FE plugin loader system
  to [fetch data from the plugin's iframe](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage)
- Code should be executed in an iframe sandbox.
- Requests from the sandbox should be limited.
- `CapitalCamelCasePluginName` would be the name of the react element
- Glue code (generated by the plugin loader system) would render the element

## Responsibility of this module

- Generate the untrusted modules necessary
- Bind together the client's code

# Project Directory Structure

```
dr_back_plugins_buildenv/
 ├─ honeypot/
 │   ├─ importme.privileged.txt
 │   └─ importme.txt
 ├─ overlay/
 │   ├─ src/
 │   │   ├─ index.jsx
 │   │   └─ index.scss
 │   ├─ .babelrc
 │   ├─ .gitignore
 │   ├─ package-lock.json
 │   ├─ package.json
 │   └─ webpack.config.js
 ├─ plugins_commons/
 │   ├─ .github/
 │   │   └─ workflows/
 │   │       └─ unit-testing.yml
 │   ├─ src/
 │   │   ├─ model/
 │   │   │   ├─ packet/
 │   │   │   │   ├─ build_context.rs
 │   │   │   │   ├─ build_queued.rs
 │   │   │   │   ├─ build_status.rs
 │   │   │   │   └─ mod.rs
 │   │   │   ├─ mod.rs
 │   │   │   └─ util.rs
 │   │   ├─ tests/
 │   │   │   ├─ model/
 │   │   │   │   ├─ packet/
 │   │   │   │   │   ├─ build_context.json
 │   │   │   │   │   ├─ build_context.malicious.abs.json
 │   │   │   │   │   ├─ build_context.malicious.pt.json
 │   │   │   │   │   ├─ build_context.rs
 │   │   │   │   │   ├─ build_status.rs
 │   │   │   │   │   └─ mod.rs
 │   │   │   │   └─ mod.rs
 │   │   │   └─ mod.rs
 │   │   └─ lib.rs
 │   ├─ .gitignore
 │   ├─ Cargo.lock
 │   ├─ Cargo.toml
 │   └─ README.md
 ├─ src/
 │   ├─ test/
 │   │   └─ mod.rs
 │   ├─ utils/
 │   │   ├─ error.rs
 │   │   ├─ fs.rs
 │   │   └─ mod.rs
 │   ├─ builder.rs
 │   ├─ main.rs
 │   ├─ server.rs
 │   └─ spawner.rs
 ├─ .dockerignore
 ├─ .gitignore
 ├─ .gitmodules
 ├─ Cargo.lock
 ├─ Cargo.toml
 ├─ Dockerfile
 ├─ README.md
 ├─ docker-compose.yml
 ├─ precommit.sh
 └─ rustfmt.toml
```
