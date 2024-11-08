# 虛擬化<br>Virtualization

將一個或多個實體資源，如硬體、作業系統、應用程式或資料儲存，透過軟體技術的手段，將其抽象化、隔離化、統合化及自動化，形成一個或多個虛擬的資源，讓使用者可以彈性地使用和管理這些虛擬化的資源，並且可以在不影響其他虛擬化資源的情況下進行管理和配置

<https://gitlab.com/libre-knowledge/virtualization>  
[![GitLab CI 持續整合流程狀態標章](https://gitlab.com/libre-knowledge/virtualization/badges/main/pipeline.svg?ignore_skipped=true "點擊查看 GitLab CI 持續整合流程的運行狀態")](https://gitlab.com/libre-knowledge/virtualization/-/commits/main) [![「檢查專案中的潛在問題」GitHub Actions 作業流程狀態標章](https://github.com/libre-knowledge/virtualization/actions/workflows/check-potential-problems.yml/badge.svg "本專案使用 GitHub Actions 自動化檢查專案中的潛在問題")](https://github.com/libre-knowledge/virtualization/actions/workflows/check-potential-problems.yml) [![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white "本專案使用 pre-commit 檢查專案中的潛在問題")](https://github.com/pre-commit/pre-commit) [![REUSE 規範遵從狀態標章](https://api.reuse.software/badge/gitlab.com/libre-knowledge/virtualization "本專案遵從 REUSE 規範降低軟體授權合規成本")](https://api.reuse.software/info/gitlab.com/libre-knowledge/virtualization)

## 基本概念

以下列舉本主題相關的基本概念說明資源：

### 主端<br>Host

運行虛擬化解決方案的主機，負責提供運算資源給[客端](#客端-guest)使用，一個虛擬化主端系統可以運行多個[客端](#客端-guest)環境

### 客端<br>Guest

於[主端](#主端-host)上運行的虛擬運算環境，與主端系統有一定程度的隔離，可以存取的資源受限

### 虛擬機監管器<br>Virtual Machine Hypervisor / Virtual Machine Monitor(VMM)

於[主端](#主端-host)運算環境運行，管理並分配硬體資源給[客端](#客端-guest)的系統或應用

### 原生/裸機型虛擬機監管器<br>Native/Bare-metal hypervisor

直接運行於主機硬體上（而非一般用途作業系統上）的虛擬機監管器，運行效能相對第二類虛擬機監管器較好

又稱為第一類虛擬機監管器(TYPE-1 Hypervisor)

### 託管型虛擬機監管器<br>Hosted hypervisor

以應用軟體的方式運行於一般用途作業系統上的[虛擬機監管器](#虛擬機監管器-virtual-machine-hypervisor-virtual-machine-monitor-vmm)，運行效能較第一類虛擬機監管器差

又稱為第二類虛擬機監管器(TYPE-2 Hypervisor)

### 硬體虛擬化<br>Hardware virtualization

模擬一硬體並將其操作轉換為相容的指令在現有的硬體上執行

### 全虛擬化<br>Full virtualization

幾乎完全模擬實際的硬體以能夠使作業系統與軟體在不經過修改適配的前提下直接運行

由於必須要翻譯所有的客端請求為主端指令故效能較差

### 伴虛擬化<br>Para-virtualization

透過與[客端](#客端-guest)作業系統特別提供的界面交互來減少需要大量運算或時間才能處理的[客端](#客端-guest)操作，藉以改善虛擬化效能的技術

需要[主端](#主端-host)[虛擬機監管器](#虛擬機監管器-virtual-machine-hypervisor-virtual-machine-monitor-vmm)與[客端](#客端-guest)作業系統支援對應的 API 才能夠使用（如 Linux）

### 硬體輔助虛擬化<br>Hardware-assisted virtualization

由中央處理器、晶片組等硬體提供，將虛擬機器的部份工作取代以提高虛擬機器運行效能的虛擬化解決方案

須硬體、韌體與[虛擬機監管器](#虛擬機監管器-virtual-machine-hypervisor-virtual-machine-monitor-vmm)支援

### 作業系統層級虛擬化<br>Operating system level virtualization

透過抽象化作業系統的功能與命名空間等隔離技術使多個客端作業系統可以與主端作業系統共用作業系統核心並同行運行的技術

## 解決方案

以下列舉本主題相關的解決方案：

### 虛擬機監管器

* ESXi  
  由 VMware 推出之支援[伴虛擬化](#伴虛擬化-para-virtualization)的[原生/裸機型虛擬機監管器](#原生裸機型虛擬機監管器nativebare-metal-hypervisor)解決方案
* Hyper-V  
  由微軟所推出之支援[伴虛擬化](#伴虛擬化-para-virtualization)的[原生/裸機型虛擬機監管器](#原生裸機型虛擬機監管器nativebare-metal-hypervisor)解決方案
* QEMU  
  支援[全虛擬化](#全虛擬化-full-virtualization)與（搭配 KVM）[伴虛擬化](#伴虛擬化-para-virtualization)的[託管型虛擬機監管器](#託管型虛擬機監管器hosted-hypervisor)解決方案
* [VirtualBox](https://gitlab.com/libre-knowledge/virtualbox)  
  由<ruby>甲骨文<rp>(</rp><rt>Oracle</rt><rp>)</rp></ruby>公司推出之具備使用者友善的圖形化操作界面、支援[伴虛擬化](#伴虛擬化-para-virtualization)的開放來源碼[託管型虛擬機監管器](#託管型虛擬機監管器hosted-hypervisor)解決方案
* Xen  
  支援[全虛擬化](#全虛擬化-full-virtualization)與（搭配 KVM）[伴虛擬化](#伴虛擬化-para-virtualization)的開放來源碼[原生/裸機型虛擬機監管器](#原生裸機型虛擬機監管器nativebare-metal-hypervisor)解決方案

### 作業系統層級虛擬化

* [Docker](https://gitlab.com/libre-knowledge/docker)  
  主流的容器實現之一
* Kubernetes
* Podman
* LXC
* LXD

### 硬體輔助虛擬化

* VT-x/AMD-V
* VT-d
* VT-c
* AMD-Si
* Extended Page Tables(Second Level Address Translation (SLAT))

### 虛擬化資源編排工具

* Docker Compose
* [Vagrant 開發環境建置與統合工具](https://gitlab.com/libre-knowledge/vagrant)  
  快速建置相同的開發環境，避免團隊成員間環境不一致造成開發阻礙

## 參考資料

以下列舉撰寫本主題內容時所參考的第三方資源：

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
* [3.3. Hardware vs. Software Virtualization](https://docs.oracle.com/en/virtualization/virtualbox/6.0/admin/hwvirt.html)
* [Understanding the Virtualization Spectrum - Xen](https://wiki.xenproject.org/wiki/Understanding_the_Virtualization_Spectrum)  
  說明全虛擬化與伴虛擬化的差異，與 Xen 所支援的實作方式

---

本主題為[自由知識協作平台](https://gitlab.com/libre-knowledge/libre-knowledge)的一部分，除部份特別標註之經合理使用(fair use)原則使用的內容外允許公眾於授權範圍內自由使用

如有任何問題，歡迎於本主題的[議題追蹤系統](https://gitlab.com/libre-knowledge/virtualization/-/issues)創建新議題反饋
