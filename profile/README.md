<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/HelixOS-Org/helix/main/assets/logo-banner.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/HelixOS-Org/helix/main/assets/logo-banner.svg">
  <img alt="Helix OS" src="https://raw.githubusercontent.com/HelixOS-Org/helix/main/assets/org-banner.svg" width="560">
</picture>

<br/>

**Rethinking the kernel — one trait at a time.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](https://github.com/HelixOS-Org/helix/blob/main/LICENSE)
[![Rust: nightly](https://img.shields.io/badge/rust-nightly-orange?style=flat-square&logo=rust)](https://github.com/HelixOS-Org/helix/blob/main/rust-toolchain.toml)
[![Target: x86_64](https://img.shields.io/badge/target-x86__64--unknown--none-green?style=flat-square)](https://github.com/HelixOS-Org/helix)

</div>

---

Helix is a **modular, capability-based operating system kernel** written entirely in Rust.
It targets bare metal (`x86_64-unknown-none`) with zero reliance on the standard library —
every crate is `#![no_std]`, every subsystem is a trait, and every implementation is a
hot-swappable module.

The kernel is not a monolith that happens to be extensible. It is an **extensible framework
that happens to be a kernel.**

### 🧬 What Makes Helix Different

<table>
<tr>
<td width="50%">

**🔩 Mechanism, Not Policy**

The trusted computing base provides interrupt dispatch,
capability validation, and context switching — nothing more.
Scheduling policies, memory allocation strategies, and
filesystem behavior all live in replaceable modules.

</td>
<td width="50%">

**♻️ Hot-Reload at Runtime**

Modules can be replaced while the kernel is running: state
snapshot → atomic swap → ABI compatibility check → automatic
rollback on failure. No reboot required.

</td>
</tr>
<tr>
<td width="50%">

**🛡️ Self-Healing by Default**

A watchdog + health monitor + recovery manager pipeline
detects crashed or hung modules, restarts them, and migrates
state — without bringing down the system.

</td>
<td width="50%">

**🧠 NEXUS Intelligence**

A kernel-level observability engine with failure prediction,
anomaly detection, causal graphs, and an evolution sandbox
that lets the kernel learn from its own execution.

</td>
</tr>
</table>

### 📦 The Stack

| Layer | Component | Description |
|:------|:----------|:------------|
| **Boot** | Limine · UEFI · Multiboot2 | Three bootloader frontends — pick the one your hardware needs |
| **HAL** | Trait-driven abstraction | `Cpu`, `Mmu`, `InterruptController`, `Firmware` — implement four traits to port Helix |
| **Core** | Orchestrator + Syscall + IPC | Policy-free TCB: lifecycle, capability broker, interrupt routing |
| **Subsystems** | Memory · Execution · DIS · NEXUS · Init | Trait-based frameworks — plug in any conforming implementation |
| **Modules** | Schedulers · Allocators · Drivers | Hot-swappable, ABI-versioned, fault-isolated |
| **Filesystem** | HelixFS | CoW, B+tree indexing, journaling, encryption, snapshots |
| **Graphics** | Lumina (21 crates) | `no_std` GPU API — shader compiler, render graph, PBR, ray tracing, SPIR-V codegen |

### 🚀 Get Started

```bash
git clone https://github.com/HelixOS-Org/helix.git
cd helix
make run    # builds + boots in QEMU
```

### 🤝 Contributing

We welcome contributions of all sizes — from typo fixes to new subsystems.
Read our **[Contributing Guide](https://github.com/HelixOS-Org/helix/blob/main/CONTRIBUTING.md)**
and our **[Code of Conduct](https://github.com/HelixOS-Org/helix/blob/main/CODE_OF_CONDUCT.md)**
before opening your first PR.

<div align="center">

**[📖 Wiki](https://github.com/HelixOS-Org/helix/wiki)** · **[🐛 Issues](https://github.com/HelixOS-Org/helix/issues)** · **[💬 Discussions](https://github.com/HelixOS-Org/helix/discussions)** · **[🔒 Security](https://github.com/HelixOS-Org/helix/blob/main/SECURITY.md)**

</div>
