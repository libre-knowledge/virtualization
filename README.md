# 虛擬化 Virtualization

將一個或多個實體資源，如硬體、作業系統、應用程式或資料儲存，透過軟體技術的手段，將其抽象化、隔離化、統合化及自動化，形成一個或多個虛擬的資源，讓使用者可以彈性地使用和管理這些虛擬化的資源，並且可以在不影響其他虛擬化資源的情況下進行管理和配置

[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white "本專案使用 pre-commit 檢查專案中的潛在問題")](https://github.com/pre-commit/pre-commit) [![REUSE 規範遵從狀態標章](https://api.reuse.software/badge/gitlab.com/libre-knowledge/virtualization "本專案遵從 REUSE 規範降低軟體授權合規成本")](https://api.reuse.software/info/github.com/libre-knowledge/virtualization)

## 基本概念

### 主端<br>Host

運行虛擬化解決方案的主機，負責提供運算資源給[客端](#客端-guest)使用，一個虛擬化主端系統可以運行多個[客端](#客端-guest)環境

### 客端<br>Guest

於[主端](#主端-host)上運行的虛擬運算環境，與主端系統有一定程度的隔離，可以存取的資源受限

### 虛擬化監管器<br>Hypervisor / Virtual Machine Monitor(VMM)

於[主端](#主端-host)運算環境運行，管理並分配硬體資源給[客端](#客端-guest)的系統或應用

### 原生/裸機型虛擬化監管器（第一類虛擬化監管器）<br>Native/Bare-metal hypervisor(TYPE-1 Hypervisor)

直接運行於主機硬體上（而非一般用途作業系統上）的虛擬化監管器，運行效能相對第二類虛擬化監管器較好

### 託管型虛擬化監管器（第二類虛擬化監管器）<br>Hosted hypervisor(TYPE-2 Hypervisor)

以應用軟體的方式運行於一般用途作業系統上的[虛擬化監管器](#虛擬化監管器-hypervisor-virtual-machine-monitor-vmm)，運行效能較第一類虛擬化監管器差

### 硬體虛擬化<br>Hardware virtualization

模擬一硬體並將其操作轉換為相容的指令在現有的硬體上執行

### 全虛擬化<br>Full virtualization

幾乎完全仿真實際的硬體以能夠使作業系統與軟體在不經過修改適配的前提下直接運行

由於必須要翻譯所有的客端請求為主端指令故效能較差

相關的解決方案：

* QEMU（未使用等[伴虛擬化](#伴虛擬化-para-virtualization)支援的情況下）

### 伴虛擬化<rp>(</rp><rt>Para-virtualization</rt><rp>)

透過與[客端](#客端-guest)作業系統特別提供的界面交互來減少需要大量運算或時間才能處理的[客端](#客端-guest)操作，藉以改善虛擬化效能的技術

需要[主端](#主端-host)[虛擬化監管器](#虛擬化監管器-hypervisor-virtual-machine-monitor-vmm)與[客端](#客端-guest)作業系統支援對應的 API 才能夠使用（如 Linux）

相關方案：

* VMware ESXi
* Hyper-V
* QEMU（搭配 KVM）
* Xen

## 解決方案

* Docker
* LXC
* LXD
* Oracle VirtualBox
* QEMU
* Xen

## 參考資料

* [虛擬化 - 維基百科，自由的百科全書](https://zh.wikipedia.org/zh-tw/%E8%99%9B%E6%93%AC%E5%8C%96)  
  [Virtualization - Wikipedia](https://en.wikipedia.org/wiki/Virtualization)  
  維基百科條目
* [仿真器 - 維基百科，自由的百科全書](https://zh.wikipedia.org/wiki/%E4%BB%BF%E7%9C%9F%E5%99%A8)
* [Hypervisor - 維基百科，自由的百科全書](https://zh.wikipedia.org/wiki/Hypervisor)
* [Xen - 維基百科，自由的百科全書](https://zh.wikipedia.org/wiki/Xen)
* [terminology - Simulator or Emulator? What is the difference? - Stack Overflow](https://stackoverflow.com/questions/1584617/simulator-or-emulator-what-is-the-difference/1584701#1584701)
* [Virtualization - Wikipedia](https://en.wikipedia.org/wiki/Virtualization)
* [para- - Wiktionary](https://en.wiktionary.org/wiki/para-#Etymology_1)
* [Paravirtualization - Wikipedia](https://en.wikipedia.org/wiki/Paravirtualization)
* [QEMU - Wikipedia](https://en.wikipedia.org/wiki/QEMU)
* [Hardware virtualization - Wikipedia](https://en.wikipedia.org/wiki/Hardware_virtualization)

---

本主題為[自由知識協作平台](https://libre-knowledge.github.io/)的一部分，除部份特別標註之經合理使用(fair use)原則使用的內容外允許公眾於授權範圍內自由使用

如有任何問題，歡迎於本主題的[議題追蹤系統](https://github.com/libre-knowledge/virtualization/-/issues)創建新議題反饋
