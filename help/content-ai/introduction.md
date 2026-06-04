---
title: AEM Content Ai概述
description: 了解什么是AEM Content AI，它为什么重要，以及如何开始为您的AEM as a Cloud Service环境启用和控制它。
topic: Overview
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM内容人工智能，概述，内容源，语义搜索，获取， Cloud Manager
source-git-commit: 9b3c63be1aa95339086ee5994cd4dd7cdfa7e746
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---


# AEM Content AI — 简介

## 智能内容，通过设计支持AI {#ai-ready}

客户开始通过AI与品牌见面，然后再与网站见面。聊天助理、AI概述、代理、对话式搜索、AI门卫 — 所有这些人都代表品牌检索、总结和呈现品牌内容。他们所说的内容只有准确、最新和品牌化，才会是他们可以触及的内容。
这是AEM Content AI专为这种转变而构建的功能。它将品牌内容视为AI体验运行的基本事实，并为AEM客户提供了工具，以便在创作端更快地创建基本事实，并在发布端为面向消费者的AI驱动型体验干净地提供该事实。

**在创作端**，AEM Content AI基于在批准的品牌源中创建。 AI辅助创作、跨现有页面内容、片段和资源的自然语言发现以及品牌感知生成，使团队无需离开AEM即可为新受众、地区和渠道生成变体，并且不会偏离已批准的内容。

**在发布端**，相同的内容是结构化的、可控的，可供AI使用。 片段、元数据、分类和批准的源以可充满信心地使用检索系统、代理和对话界面的形式显示 — 因此，当AI代表品牌时，它会说出品牌的真相。

### 对AEM客户的意义 {#what-it-means}

已获批准的内容是品牌避免幻觉的防线。当AI基于受管理的AEM内容时，默认情况下答案保持准确、最新且符合品牌标准。
创作速度与人工智能时代的需求保持同步。团队为创作体验中的更多受众和时刻生成文案和图像 — 从批准的来源而不是从空白开始。
发现就像人和机器实际要求的那样。跨资产、片段、页面和表单的基于意图的自然语言搜索可将现有内容转换为可重复使用的内容。
Personalization通过重复使用而不是重复进行扩展。受控制的组件将重组为变体，而不是乘以不受跟踪的副本。
发布渠道现在包括AI表面。内容以人类、代理和人工智能媒介的体验都可以消费的形式提供 — 没有针对每一种的单独管道。

**更重要的一点：现有的受信任品牌内容比以往任何时候都更有价值。 在AEM中已有的每个经批准的片段、资源和页面都成为人工智能驱动型体验所依赖的基本事实，而AEM Content AI正是使该库可重用、可发现和准备好支持后续功能的原因。**

## AEM Content AI概览 {#at-a-glance}

AEM内容人工智能的结构为四层栈叠 — 每个层都构建在下面的某个层上，从基础的可信内容到它支持的顶部代理体验。

![四层AEM Content AI架构栈栈的示意图：基础上的Content AI源、基础上的Content AI服务、Agentic Content Orchestration以及顶部的代理体验编排](../assets/content-ai-four-layer-architecture-stack.png)

*自下而上地阅读栈栈 — 从基础上的受信任内容到其顶部的代理体验。*

1. 内容人工智能源
内容源是AEM Content AI中连接到可信内容主体的托管实体。 内容Source可以引用受AEM管理的内容类型（如资产、内容片段、页面、表单、元数据和分类）以及非AEM源（如第三方网站、知识库或文档门户）。 每个Content Source都自动矢量化，并在语义上丰富了电源检索、接地和对话式人工智能体验。 只需定义一次内容源，即可通过内置的自动刷新和更新功能跨内容人工智能API重复使用它们。

1. Content AI基础服务
API和服务在品牌内容的上下文中支持语义智能和创成人工智能。 使用内容人工智能源，这些服务能够检索、生成、品牌感知变化和优化，所有这些都基于客户的批准内容。

1. 代理内容编排
通过自然语言将用例驱动的内容需求转化为协调操作的MCP和代理。 该层允许作者和其他代理以简单的语言描述他们需要的内容，并协调正确的基础服务来实现它。

1. Agentic Experience Orchestration
当智能品牌内容大规模满足AI要求时出现的创新用例。 AEM解决方案本身基于这些基础服务而构建，客户可以直接使用相同的API来基于其自己的内容构建自己的代理体验。 从AI支持的内容供应链到对话用户历程，此层是受管内容成为竞争优势的地方。

这些层通过设计相连：每个AI服务都从内容基础中获取，并且生成的所有内容流回同一个受控系统 — 因此作者端创建和发布端交付共享一个真实来源。

## AEM Content AI的实际操作 {#action}

获取有效的Content AI集成涉及两个任务：

### &#x200B;1. 为您的AEM环境启用内容人工智能 {#enable}

**先决条件：**&#x200B;在开始使用内容人工智能之前，您需要包含在AEM as a Cloud Service环境范围内的API凭据。 请参阅[设置Adobe Developer Console项目](setup-adc-project.md)。

### &#x200B;2. 控制您的内容AI源 {#control}

设置和管理内容人工智能源以启用基于人工智能的体验，请参阅[控制内容源](contentsources.md)。

## 了解Content AI API  {#apis}

探索AEM Content AI的功能范围 — API展示了平台的全部潜力。 查看[内容人工智能API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/)。
