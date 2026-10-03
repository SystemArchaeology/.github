<div align="center">

<img src="./banner.png" alt="System Archaeology — Under the abstraction" width="820">

# System Archaeology

### Under the abstraction.

</div>

---

**System Archaeology** is a collection of experiments, tools, documentation, and research projects focused on understanding how computing systems actually work.

We don't stop at the command, API, GUI, or abstraction.

We dig underneath it.

From **C, Linux, and Windows internals** to **networking, virtualization, storage, Kubernetes, hardware, documentation systems, and AI tooling**, the goal is to build things, take them apart, trace their behavior, and document what we discover.

---

## What We Do

We explore technology from the layers above the abstraction down to the machinery underneath:

```text
Applications
     ↓
Libraries & APIs
     ↓
System Calls
     ↓
Operating System
     ↓
Kernel
     ↓
Drivers
     ↓
Hardware
     ↓
Machine
```

The projects in this organization are therefore not simply "tools".

Many are **laboratories**.

They exist to answer questions such as:

* What actually happens when a Linux command runs?
* What actually happens when a Windows command or `.exe` runs?
* How does a C program become a process?
* What happens between a system call and the kernel?
* How does a Win32 call reach the NT kernel?
* What does the Windows registry really store, and where does it live on disk?
* How do you install, image, and automate Windows reproducibly — from one machine to a whole fleet?
* What is really inside a Kubernetes cluster?
* How do containers reach the kernel?
* How does a tape library actually work?
* What happens during Linux boot — and how does Windows boot differ?
* How do filesystems, storage devices, and backup systems interact?
* How can complex technical documentation be made searchable, verifiable, and reproducible?
* How can AI assist engineers without inventing technical facts?

---

# Projects

## 🐧 Linux & Systems

Projects exploring Linux, Unix, C programming, system programming, kernel internals, boot processes, tracing, and low-level behavior.

This runs deep and long: a complete **Linux From Scratch** system built from source as a 2005 graduation project, hands-on work from the classic **Red Hat Linux 8/9** era through to **RHEL 8 and 9**, and years spent **teaching Linux**.

### Kernel & Systems Research

Experiments and educational material for understanding the Linux kernel from the inside out.

Topics include:

* kernel architecture
* processes and scheduling
* memory management
* system calls
* filesystems
* networking
* device drivers
* kernel modules
* eBPF
* tracing and observability
* boot and initialization

---

## 💻 Systems Programming

A long-term exploration of **C, Unix APIs, POSIX, assembly, executable formats, and operating-system interfaces**.

The philosophy is simple:

> Learn the abstraction, then learn what is underneath it.

The learning path starts with C and progressively moves toward:

```text
C
 ↓
POSIX / Unix
 ↓
Processes
 ↓
System Calls
 ↓
ELF & Linking
 ↓
Assembly
 ↓
Kernel Interfaces
 ↓
Kernel Internals
 ↓
Hardware
```

---

# 🪟 Windows

Windows gets the same treatment as Linux: not a black box you click through, but a documented, debuggable, **deployable** system — understood from the Win32 call at the top down to the hardware, and from a single boot sector out to a whole fleet.

### Internals

A documented, debuggable system with its own well-defined layers. The path from a user-mode call to the machine:

```text
Win32 / .NET Applications
        ↓
Win32 API  (kernel32, user32, gdi32)
        ↓
Native API  (ntdll.dll)
        ↓
System Service Dispatch  (syscall)
        ↓
Executive & Kernel  (ntoskrnl.exe)
        ↓
HAL
        ↓
Hardware
```

Hands-on, this has meant **Windows API programming in C**, plenty of time in the **registry**, and taking **binaries** apart — the PE format, DLLs, and what an `.exe` really is. The broader architecture we keep digging into:

* the NT kernel, the executive, and the HAL
* processes, threads, jobs, and the scheduler
* the virtual memory manager and working sets
* the **registry** — what it stores and where (hives on disk)
* **services** and the Service Control Manager
* the Win32 subsystem and the **native API** (`ntdll`)
* the **PE / COFF** executable format, image loading, and DLLs
* the Windows **driver model** and the I/O manager
* **ETW**, performance counters, and tracing
* kernel debugging and crash dumps with **WinDbg**
* the Windows boot process (UEFI → `bootmgr` → `winload` → `ntoskrnl`)
* **WMI, COM**, and PowerShell
* **WSL, Hyper-V**, and containers on Windows

The questions mirror the Linux ones:

* How does a Win32 call become a syscall into the NT kernel?
* What is really inside a crash dump?
* How do Hyper-V and WSL reach the hardware?
* Where does Windows actually keep its configuration — and why?

### Deployment, Imaging & Automation

Windows isn't only something you debug — it's something you **deploy**, and that layer has its own depth. This area is grounded in long hands-on experience, from Windows 98 through current Windows Server:

* **Unattended installation** — answer-file-driven, scripted setup: from the Windows 98 and XP era (answer files served from **floppy** and **CD-ROM**, boot-and-install media) through to modern `unattend.xml` and **Sysprep** imaging.
* **Boot & install media** — bootable install CDs, **live CDs**, and **multiboot** discs; low-level disk preparation with `gdisk` (rather than `fdisk`); and **USB flash-drive** installers for both Windows and Linux (since 2009).
* **Imaging & cloning** — drive-image cloning with **Norton Ghost** (Windows 98, then XP) on real hardware, alongside Sysprep-generalized images.
* **Network OS deployment** — **PXE**-booted, image-based rollout over the network with **RIS**, then **WDS** and **MDT** task sequences.
* **Application deployment** — silent and scripted installs, including GUI automation with **AutoIt**.
* **Active Directory & server services** — building and operating AD on Windows Server **2000, 2003, 2008 and later**, with the supporting roles (DNS, DHCP, Group Policy, file and print, and more).

The philosophy is the same as everywhere else in the lab: **automate it, make it reproducible, and understand every layer — from the boot sector up to the domain.**

---

# 🌐 Networking

Experiments and educational projects covering networking from the packet level upward.

Areas include:

* Ethernet
* TCP/IP
* DNS
* HTTP
* routing
* sockets
* packet analysis
* network programming
* Linux networking
* Windows networking
* network troubleshooting
* network security

The emphasis is on understanding **what actually happens on the wire**.

It's also a long-running teaching area — **CCNA-level routing and switching** — backed by emulation and real labs:

* **Network emulation** — Cisco topologies with **Dynamips** and **GNS3** since the mid-2000s, back when you calculated the **Idle-PC** value by hand with a separate tool (the early `gns3.net` era).
* **Wireless** — self-taught on virtual machines, then turned into a professional service.

---

# ☸️ Kubernetes & Containers

Kubernetes is approached from the bottom up rather than treating it as a black box.

The goal is to understand the components underneath Kubernetes:

```text
Kubernetes
    ↓
kubelet
    ↓
containerd
    ↓
runc
    ↓
Linux namespaces
    ↓
cgroups
    ↓
Linux kernel
```

Projects and experiments investigate:

* Kubernetes components
* containers
* namespaces
* cgroups
* container runtimes
* networking
* storage
* cluster architecture
* the binaries that make Kubernetes work

---

# 💾 Storage, Tape & Backup

Projects exploring storage technology and enterprise backup systems.

One major area is the construction of a complete Linux-based tape laboratory involving:

* MHVTL
* virtual tape libraries
* SCSI generic devices
* LTO drives
* tape changers
* backup software — **Bareos**, **Veritas NetBackup**, and **EMC NetWorker**
* PostgreSQL
* backup catalogs
* disaster recovery
* bare-metal recovery

The objective is not simply to configure backup software, but to understand the entire chain:

```text
Backup Application
       ↓
Backup Catalog
       ↓
Tape Management
       ↓
SCSI
       ↓
Tape Drive
       ↓
Tape
```

### `mhvtl-console`

A **web console and command line for MHVTL**, the Linux virtual tape library —
[github.com/abdelhaleemahmed/mhvtl-console](https://github.com/abdelhaleemahmed/mhvtl-console).
It makes a virtual tape lab easy to drive without hand-running the low-level `mtx` / `sg` commands.

---

# 🖥️ Virtualization

### `vmctl`

A Terraform-inspired command-line tool for managing local virtual machines.

The project is designed around:

* declarative VM definitions
* YAML / JSON configuration
* validation
* dry-run operation
* cloning
* replication
* Git-managed infrastructure
* hypervisor capability checking

The initial target is VirtualBox, with a longer-term goal of supporting KVM/QEMU and Hyper-V.

### The lab bench

Virtualization is where everything else here gets built, broken, and re-tested — and it goes back a long way:

* **VMware** — from the early Workstation 3.x and **Server 1 & 2** days through to the present.
* **Microsoft Virtual PC**, and later **Hyper-V**.
* **VirtualBox** — the current daily driver; custom **Vagrant boxes** (with my own provisioning) are being published soon.

These benches run Windows and Linux alike — the same imaging, cloning, and automation discipline applied to both.

### In production

Beyond the home lab, this includes real enterprise and telecom systems:

* **Zain Sudan (telecom)** — built the operator's virtualization platform from its first steps through to a working production platform.
* **Enterprise hardware** — hands-on with **Sun SPARC**, **IBM AIX on POWER5**, and **HP** and **Sun blade** systems, and standing these environments up in emulation (QEMU-backed, through GNS3) to study them away from the physical boxes.

---

# 📚 Documentation Engineering

Technical documentation is treated as an engineering system rather than simply a collection of Markdown files.

Projects explore:

* Sphinx
* MkDocs
* Docusaurus
* Diátaxis
* Mermaid
* requirements traceability
* documentation validation
* searchable documentation
* technical claim verification
* reproducible documentation builds

We are particularly interested in the question:

> **How do you know that technical documentation is actually correct?**

---

# 🤖 Local AI & Technical Knowledge Systems

Experiments with local AI systems for engineering and technical documentation.

Areas include:

* local LLMs
* RAG
* embeddings
* technical document retrieval
* offline knowledge bases
* code assistance
* documentation assistants
* local text-to-speech
* Arabic technical language support

The goal is to build AI systems that are useful **without sacrificing technical accuracy or traceability**.

A core principle:

> **If the system doesn't know, it should say that it doesn't know.**

---

# 🔧 Developer Tools

Small utilities designed to solve practical engineering problems.

Some projects are deliberately small.

Others are experiments that may eventually grow into full tools.

Examples include:

### `slimv`

A video-library optimization tool designed to reduce storage consumption while preserving visual quality.

The philosophy:

```text
Measure
  ↓
Encode
  ↓
Measure again
  ↓
Compare
  ↓
Only then remove the original
```

### `ServeWise`

A lightweight local web server designed primarily for previewing and diagnosing documentation websites.

---

# 🔬 Hardware & Electronics

Experiments that move below the operating system into physical computing.

Topics include:

* electronics
* transistor models
* Ebers–Moll
* circuit analysis
* SPICE
* microcontrollers
* Arduino
* CPUs
* memory
* buses
* hardware interfaces

The same philosophy applies:

> Don't just use the component. Understand the model underneath it.

---

# 🧪 The Laboratory

Many projects in this organization are experimental.

They may begin as:

```text
Question
   ↓
Hypothesis
   ↓
Small experiment
   ↓
Measurement
   ↓
Implementation
   ↓
Failure
   ↓
Investigation
   ↓
Documentation
   ↓
Understanding
```

Failure is part of the process.

A broken experiment is often more educational than a successful one.

---

# 🗿 Why "System Archaeology"?

Modern computing is built on layers of abstractions.

Each layer hides enormous amounts of complexity.

That is useful.

But sometimes you need to dig through those layers.

A command hides a system call.

A system call hides kernel code.

The kernel hides hardware operations.

A Win32 API call hides the native API, a syscall, and the NT kernel.

A container hides namespaces and cgroups.

Kubernetes hides container runtimes.

A documentation site hides a build system.

An AI assistant hides models, embeddings, retrieval, and inference.

**System Archaeology is about digging through those layers.**

---

# Under the abstraction.

We build.

We measure.

We trace.

We break things.

We investigate.

We document.

And then we go one layer deeper.

---

## Principles

**Understand before automating.**

**Measure before optimizing.**

**Read the source when documentation isn't enough.**

**Prefer reproducible experiments over assumptions.**

**Don't hide complexity when understanding it matters.**

**Document what was actually observed.**

**Distinguish facts, measurements, hypotheses, and conclusions.**

**Never let an abstraction become an excuse to stop learning.**

---

## Status

This organization is an evolving collection of:

* 🔬 experiments
* 🧰 tools
* 📚 documentation
* 🧪 laboratories
* 📝 research notes
* 🖥️ infrastructure projects
* 🤖 local AI experiments

Some projects are mature.

Some are prototypes.

Some exist primarily to answer a question.

That's intentional.

---

<div dir="rtl" align="right">

## بالعربية

**System Archaeology** مجموعة من التجارب والأدوات والتوثيق ومشاريع البحث، هدفها فهم كيف تعمل أنظمة الحوسبة فعلاً. لا نتوقف عند الأمر أو الواجهة البرمجية أو الواجهة الرسومية أو التجريد — بل نحفر تحته.

من **لغة C وأعماق لينكس وويندوز** إلى الشبكات والمحاكاة الافتراضية والتخزين وKubernetes والعتاد وأنظمة التوثيق وأدوات الذكاء الاصطناعي: نبني الأشياء، ونفكّكها، ونتتبّع سلوكها، ونوثّق ما نكتشفه — ثم ننزل طبقةً أعمق.

</div>

---

<div align="center">

## System Archaeology

**Under the abstraction.**

<sub><code>$ under --the-abstraction</code></sub>

</div>
