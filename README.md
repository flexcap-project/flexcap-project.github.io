* * *
**News**
- 04/2024 We will present a talk (slides <a href="assets/cheritech24-presentation.pdf">here</a>, video [here](https://www.youtube.com/watch?v=ZMmzw9AWwUc) and a <a href="assets/cheritech24-poster.pdf">poster</a> at [CheriTech'24](https://www.cl.cam.ac.uk/research/security/ctsrd/cheri/workshops/2024cheritech/).
- 04/2024 We are working on supporting multi-process applications in single address space operating systems with CHERI, check out this [early demo](fork-demo.md).
- 11/2023 We will be presenting a poster, entitled <a href="assets/FlexCap_Poster.pdf">"FlexCap: Software Compartmentalisation Trade-Offs with Hardware Capabilities"</a> at [DSbD All Hands](https://www.dsbd.tech/event/dsbd-all-hands-2/).
- 10/2023 We have made available the source for FlexOS on Morello and the applications run in our paper *Software Compartmentalization Trade-Offs with Hardware Capabilities* [here](https://github.com/jkressel/flexos-morello-hybrid).
- 09/2023 Our paper entitled "[Software Compartmentalization Trade-Offs with Hardware Capabilities](https://arxiv.org/abs/2309.11332)" is accepted in [PLOS'23](https://plos-workshop.org/2023/).
- 03/2023 We gave a talk at [CheriTech'23](https://www.dcs.gla.ac.uk/~jsinger/cheritech23.html) outlining our research into hybrid Morello compartmentalization with FlexOS, the slides can be found [here](https://github.com/olivierpierre/project-flexcap/blob/master/assets/CheriTech'23_FlexCap_Presentation.pdf).
- 12/2022 Our paper [Assessing the Impact of Interface Vulnerabilities in Compartmentalized Software](https://arxiv.org/abs/2212.12904) is accepted at [NDSS'23](https://www.ndss-symposium.org/ndss2023/). The artifacts (source code & data set) are open source and available [here](https://github.com/conffuzz/conffuzz).
- 11/2022 We have ported a minimal version of Unikraft on the Morello machine, check out the code [here](https://github.com/jkressel/uk-plat-morello), and our blog post on Unikraft's website [here](https://unikraft.org/blog/2022-12-01-unikraft-on-morello/).

* * *
## Table of Contents

- [Project Description](#project-description)
- [Publications & Documents](#publications--documents)
- [Software & Research Artefacts](#software--research-artefacts)
- [Contact](#contact)

## Project Description

In the FlexCap project, we propose to explore the benefits brought by hardware capabilities to operating systems' safety, performance and memory consumption. To that aim we propose to port two operating systems, [FlexOS](https://project-flexos.github.io/) and [Unikraft](https://unikraft.org/), to the ARM [Morello](https://www.arm.com/architecture/cpu/morello) platform, and investigate in that context the two main features provided by capabilities: efficient/scalable compartmentalization, and safe version of legacy programming languages through pure/hybrid capabilities.

FlexOS is a safety-oriented library operating system in which the safety/isolation strategy can be easily tailored at build time towards a specific application use case. Many safety options can be configured, including in particular the granularity of kernel/user components isolation and the hardware mechanism enforcing that isolation. We expect that leveraging the efficient compartmentalization features of hardware capabilities in FlexOS will bring significant advantages over the existing mechanisms the OS already supports (Intel Memory Protection Keys and Extended Page Tables). Due to the fine-grained memory protection capabilities offer, safety will be increased by allowing to share only the minimum amount of data for cross-compartment communications. Such communications' performance should also be enhanced compared to solutions based on data copy. Capabilities will also allow FlexOS to scale to a high number of compartments, something not possible with the currently supported mechanisms, for architectural (MPK) or performance (EPT) reasons.

A first step towards porting FlexOS to Morello will be to port FlexOS' basis, Unikraft, to the platform. Unikraft is a high-performance/low latency unikernel targeting cloud and edge applications. Unikraft's performance benefits come from the fact that, following the principle from the unikernel OS model, kernel and application code share a single, completely unprotected, address space. This obviously raises security concerns. Porting Unikraft to Morello gives us the unique opportunity to study bringing back safety into unikernels while maintaining the high degree of performance offered by that OS model. We plan to achieve that using the safety benefits brought by capabilities to legacy programming languages (Unikraft is written in C) through pure and/or hybrid capabilities.

FlexCap is part of the [Digital Security by Design](https://www.dsbd.tech/) programme, and is one of several project aiming at creating a [software ecosystem](https://www.dsbd.tech/unleash-of-the-release-enabling-the-digital-security-by-design-dsbd-ecosystem/) for the DSbD.


## Publications & Documents

### Papers

* **Software Compartmentalization Trade-Offs with Hardware Capabilities.**<br/>J. A. Kressel, H. Lefeuvre, P. Olivier.<br/>[**PLOS'23**](https://www.plos-workshop.org/2023/) [[ArXiv](https://arxiv.org/abs/2309.11332)]<br/>In this paper we present and evaluate our port of a compartmentalisation-aware operating system, [FlexOS](https://project-flexos.github.io/), to the DSbD Morello chip.
* **Assessing the Impact of Interface Vulnerabilities in Compartmentalized Software.**<br/>H. Lefeuvre, V. Bădoiu, Y. Chien, F. Huici, N. Dautenhahn, P. Olivier.<br/>[**NDSS'23**](https://www.ndss-symposium.org/ndss2023/) [[ArXiv](https://arxiv.org/abs/2212.12904)]<br/>Efficient software compartmentalisation is one of the key features enabled by Morello. In this paper we explore the specific vulnerabilities that emerge at cross-compartment boundaries when retroffiting compartmentalisation into existing monolithic software.
* **Towards (Really) Safe and Fast Confidential I/O.**<br/>H. Lefeuvre, D. Chisnall, M. Kogias, P. Olivier.<br/>[**HotOS'23**](https://sigops.org/s/conferences/hotos/2023/) [[Pure](https://pure.manchester.ac.uk/ws/portalfiles/portal/262834367/cio_hotos23.pdf)]<br/>In this paper we investigate securing the I/O interface of confidential VMs through various techniques including a multi-tier compartmentalisation approach for which the mechanisms enabled by Morello are a great fit.
* **CIVSCOPE: Analyzing Potential Memory Corruption Bugs in Compartment Interfaces.**<br/>Y. Chien, V. Bădoiu, Y. Yang, Y. Huo, K. Kaoudis, H. Lefeuvre, P. Olivier, and N. Dautenhahn.<br/>[**KISV'23**](https://kisv-workshop.github.io/) [[ACM](https://dl.acm.org/doi/10.1145/3625275.3625399)]<br/>In this paper we explore static analysis to detect interface vulnerabilities emerging in software compartmentalised with various mechanisms such as Morello.

### Talks
* **FlexCap: Exploring Hardware Capabilities in Unikernels and Flexible Isolation Oses,**<br/>P. Olivier.<br/>[**CheriTech'24**](https://www.cl.cam.ac.uk/research/security/ctsrd/cheri/workshops/2024cheritech/) <a href="assets/cheritech24-presentation.pdf">[slides]<a/><br/>In this talk we present the progress on the project so far on the topics of compartmentalisation, safe C/purecap, as well as ongoing work.
* **A Study of Fine-Grain Compartment Interface Vulnerabilities: What, Why, and What We Should Do About Them.**<br/>H. Lefeuvre.<br/>[**FOSDEM'23**](https://archive.fosdem.org/2023/) [[Video](https://mirrors.dotsrc.org/fosdem/2023/D.confidential/cc_online_vulnerabilities.mp4)]<br/>In this talk we present the results obtained as part of his [NDSS'23 paper](#papers).
* **Flexcap: Compartmentalisation on unikernels with hybrid capabilities**<br/>J. A. Kressel.<br/>[**CheriTech'23**](https://www.dcs.gla.ac.uk/~jsinger/cheritech23.html) [[Slides](https://www.dcs.gla.ac.uk/~jsinger/cheritech23_slides/jkressel_cheritech.pdf)]<br/>In this talk we present our early experience regarding the port of an OS to Morello in hybrid mode.
* **Compatibility and Isolation in Specialised Operating Systems**<br/>P. Olivier.<br/>Talk at Heriot-Watt University's [LAIV Seminar](https://laiv.uk/laiv-seminars/) [[Video](https://www.youtube.com/watch?v=1MyjYqUNvXM)] [[Slides](https://github.com/olivierpierre/project-flexcap/blob/master/assets/laiv-seminar-23-slides.pdf)]<br/>In this talk we present various research efforts, including FlexOS, the OS ported to Morello as part of FlexCap.
* **Research on Software Compartmentalisation**<br/>P. Olivier.<br/>Talk at the Crackchester student association Hacker's Hub event [[Slides](https://github.com/olivierpierre/project-flexcap/blob/master/assets/hackers-hub-23-slides.pdf)]<br/>In this talk we present the concept of software compartmentalisation as well as FlexOS.
* **FlexOS - Making OS Isolation Flexible**<br/>H. Lefeuvre.<br/>Huawei [Future Device Technology Summit 2023](http://haemod.uk/documents/conference/Huawei_Future_Device_Summit_Helsinki.pdf) [[Slides](https://github.com/olivierpierre/project-flexcap/blob/master/assets/flexos-huawei.pdf)]<br/>In this talk we present FlexOS in details.
* **Software Compartmentalization and the Challenge of Interfaces**<br/>P. Olivier.<br/>IRISA [Software Systems Security Seminar](https://seminaires-dga.inria.fr/en/sosysec-en-bref/) [[Video](http://videos.rennes.inria.fr/seminaire-SoSySec/Pierre-Olivier-8-12-2023/Seminaire-SoSySec-Pierre-Olivier-8-decembre-2023.html)] [[Slides](https://github.com/olivierpierre/project-flexcap/blob/master/assets/sosysec23-slides.pdf)]<br/>In this talk we present the concept of compartmentalisation as well as the interface safety investigation published in the [NDSS'23 paper](#papers).

### Theses

* **Exploring Software Compartmentalisation with Hardware Capabilities**<br/>J. A. Kressel, 2023, MPhil Thesis at [The University of Manchester](https://www.manchester.ac.uk/) [[PDF](https://pure.manchester.ac.uk/ws/portalfiles/portal/280560037/FULL_TEXT.PDF)]<br/>This thesis present our port of FlexOS to the Morello chip.

## Software & Research Artefacts

- Our [port](https://github.com/jkressel/uk-plat-morello) of Unikraft to Morello (hybrid capabilities mode)
- [ConfFuzz](https://conffuzz.github.io/), an exploratory fuzzer designed for uncovering interface-related vulnerabilities in compartmentalized software
  - ConfFuzz NDSS'23 paper [data set](https://github.com/conffuzz/conffuzz-ndss-data)
- FlexCap is in part an extension of [FlexOS](https://project-flexos.github.io/), an OS in which the isolation strategy is decoupled from the design


## Contact

- [Pierre Olivier](https://sites.google.com/view/pierreolivier), The University of Manchester `pierre dot olivier at manchester dot ac dot uk`

* * *

<p align="center">
  <img src="assets/uom-logo.png" height=150 style="margin:20px" />
  <img src="assets/ukri-logo.png" height=150 />
</p>
