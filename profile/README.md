## ReCasaOS — a maintained distribution of CasaOS

CasaOS is the dashboard a lot of people's first home server runs: Docker apps, files, shares and storage, on a box you keep at home. Upstream [IceWhaleTech/CasaOS](https://github.com/IceWhaleTech/CasaOS) is not archived, so it still looks alive — but the core has not been pushed since August 2025, the dashboard since September 2025, and the other five components since April 2025. IceWhale moved to a commercial product.

ReCasaOS is that distribution, and it kept shipping. Releases **v0.4.40** through **v0.4.62**.

```bash
curl -fsSL https://github.com/ReCasaOS/CasaOS-Install/releases/latest/download/install.sh | sudo bash
```

Runs on Docker 29 and Ubuntu 26, which upstream predates. Upgrades an existing install in place; amd64, arm64 and arm/v7.

### What changed

- **Independence from the vendor's infrastructure.** The geo-IP lookup that ran on every install and upgrade is gone, the Go module paths are this project's own, CI no longer pulls workflows from IceWhale, and every one of the ten packages the installer downloads is verified against a SHA-256 digest before it is extracted.
- **Security.** The file manager, Samba and package routes accepted any request from loopback with no token — which is every process on the host, including a container the App Store had just started. They require one now.
- **A dashboard on Vue 3.5** with a dark theme, where upstream sits on a version that reached end of life in 2023.
- **Two-factor authentication**, per-app `.env` editing, a Compose editor, and Samba shares restricted to an account instead of world-writable guest shares.
- **Multi-container apps treated as stacks**: a row per container, per-service update decisions, scheduled image-update checks, disk reclaim, logs and a terminal.

### Where things live

| | |
|---|---|
| [CasaOS-Install](https://github.com/ReCasaOS/CasaOS-Install) | the installer and the release bundle — **start here** |
| [CasaOS](https://github.com/ReCasaOS/CasaOS) | the core: files, shares, system |
| [CasaOS-UI](https://github.com/ReCasaOS/CasaOS-UI) | the dashboard |
| [CasaOS-AppManagement](https://github.com/ReCasaOS/CasaOS-AppManagement) | apps, Compose and the App Store |
| [CasaOS-Gateway](https://github.com/ReCasaOS/CasaOS-Gateway) · [UserService](https://github.com/ReCasaOS/CasaOS-UserService) · [LocalStorage](https://github.com/ReCasaOS/CasaOS-LocalStorage) · [MessageBus](https://github.com/ReCasaOS/CasaOS-MessageBus) · [Common](https://github.com/ReCasaOS/CasaOS-Common) | the rest |

It descends from [alvins82's fork](https://github.com/alvins82/CasaOS), which is the work that got CasaOS installing again on current systems.

---

> **Not affiliated with IceWhale.** This is an independent, community-maintained distribution of CasaOS. It is not produced, endorsed, sponsored, certified or supported by Shanghai IceWhale Technology Limited or by any of the upstream CasaOS maintainers. CASAOS is a trademark of Shanghai IceWhale Technology Limited; the name is used here only to identify the upstream project that this software is a distribution of. The App Store catalogue and the app icons remain IceWhale's, and are still curated by them.
