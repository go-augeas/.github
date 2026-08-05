<p align="center"><img src="https://raw.githubusercontent.com/go-augeas/brand/main/social/go-augeas.png" alt="go-augeas" width="640"></p>

<h1 align="center">go-augeas</h1>
<p align="center"><strong>Augeas configuration-tree editing in pure Go — parse, query and edit config files via lenses.</strong></p>

<p align="center">
  🌐 <a href="https://go-augeas.github.io">Website</a> ·
  📚 <a href="https://go-augeas.github.io/docs/">Documentation</a>
</p>

<p align="center">
  <a href="https://go-augeas.github.io/docs/"><img alt="Docs" src="https://img.shields.io/badge/docs-mkdocs--material-4F46E5?style=flat-square"></a>
  <a href="https://github.com/go-augeas/augeas/blob/main/LICENSE"><img alt="License: BSD-3-Clause" src="https://img.shields.io/badge/license-BSD--3--Clause-blue?style=flat-square"></a>
  <img alt="Go 1.26.4+" src="https://img.shields.io/badge/go-1.26.4%2B-00ADD8?style=flat-square&logo=go&logoColor=white">
  <img alt="Coverage 100%" src="https://img.shields.io/badge/coverage-100%25-1a7f37?style=flat-square">
</p>

---

go-augeas is a pure-Go (CGO_ENABLED=0) implementation of the core of Augeas, the configuration-editing tool from the Puppet ecosystem. It models configuration files as an ordered tree, exposes an XPath-like path language to query and edit that tree, and uses lenses to translate between the tree and concrete file syntax. A from-scratch pure-Go interpreter for the Augeas `.aug` lens DSL reads the entire embedded upstream lens corpus (232 modules) plus five original contrib lenses (Wireguard, Rclone, Caddyfile, Nftables, Unbound); write-back through those lenses is verified correct internally but not yet exposed via the public API. Load and save go through an injectable FileSystem seam, so parsing and error branches are covered deterministically without touching the disk. It imports only the Go standard library, holds 100% test coverage, and cross-compiles to the six 64-bit Go targets and WebAssembly.

## Repositories

| Repo | What it is |
|------|------------|
| [**augeas**](https://github.com/go-augeas/augeas) | the engine library |
| [**docs**](https://github.com/go-augeas/docs) | MkDocs Material documentation, versioned with [mike], served at [/docs/](https://go-augeas.github.io/docs/) |
| [**go-augeas.github.io**](https://github.com/go-augeas/go-augeas.github.io) | the Hugo landing page |
| [**brand**](https://github.com/go-augeas/brand) | logos and brand assets |

## Principles

- **Pure Go, zero cgo.** `CGO_ENABLED=0`; imports the Go standard library only. Cross-compiles to the
  six 64-bit Go targets (amd64, arm64, riscv64, loong64, ppc64le, s390x) and WebAssembly, linking into a static binary.
- **Faithful to the Augeas tree / path / lens model.**
- **An engine, not a service.** A small, stable Go API you embed — part of the
  pure-Go Puppet stack (siblings [go-facter](https://github.com/go-facter),
  [go-hiera](https://github.com/go-hiera), [go-pcore](https://github.com/go-pcore),
  [go-puppet](https://github.com/go-puppet)).
- **100% test coverage** including error branches, enforced as a CI gate.

BSD-3-Clause.

[mike]: https://github.com/jimporter/mike
