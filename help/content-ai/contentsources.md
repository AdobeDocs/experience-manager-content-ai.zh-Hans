---
title: 设置和管理您的内容人工智能源
description: 了解如何在 Cloud Manager 中配置 AEM 内容人工智能，包括设置您的第一个内容源并触发内容获取。
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM 内容人工智能、内容人工智能源、内容获取、Cloud Manager、Adobe Developer Console
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
source-git-commit: 1364d35876ef0fcc502a3d02f8025ee7df067daf
workflow-type: tm+mt
source-wordcount: '1671'
ht-degree: 76%
---

# 设置和管理您的内容人工智能源

本指南将引导您在 Cloud Manager 中设置内容人工智能源，包括满足先决条件、创建内容源，以及确认内容已建立索引并可供使用。

## 先决条件 {#prerequisites}

开始之前，请确保满足以下条件：

* 您拥有一个处于活动状态的 Cloud Manager 程序，并且其中至少包含一个 AEM as a Cloud Service 环境。
* 您具有Cloud Manager产品配置文件并且可以登录到Cloud Manager — 请参阅下面的[访问Cloud Manager](#cloud-manager-access)。
* 您的用户已分配到目标环境的 **AEM 用户**&#x200B;产品轮廓，该轮廓允许用户查看内容源。
* 您的用户已分配到目标环境的 **AEM 管理员**&#x200B;产品轮廓，该轮廓允许用户创建和编辑内容源。 仅拥有 Cloud Manager 访问权限并不足够，请参阅下文的[将用户分配到 AEM 产品轮廓](#assign-product-profile)。
* 环境产品轮廓已在 **Adobe Admin Console** 中完成配置。

## 访问Cloud Manager {#cloud-manager-access}

要打开&#x200B;**[!UICONTROL Content AI配置]**&#x200B;选项卡，您需要访问Cloud Manager UI。 您组织的[!DNL Adobe Admin Console]管理员（系统管理员或产品管理员）授予此访问权限。

1. 联系您的[[!DNL Adobe Admin Console]](https://adminconsole.adobe.com/)管理员。 如果您还不是组织的成员，请要求管理员添加您的Adobe ID或电子邮件地址。
1. 要求管理员为您分配一个适用于组织的AEM as a Cloud Service项目的Cloud Manager产品配置文件：

   | 产品配置文件 | 它允许 |
   | --- | --- |
   | **[!UICONTROL 业务负责人]** | 管理程序。 具有广泛的Cloud Manager权限，包括&#x200B;**[!UICONTROL 管理访问权限]**。 |
   | **[!UICONTROL 部署管理员]** | 管理环境、部署和管道。 |
   | **[!UICONTROL 项目管理员]** | 管理团队设置和项目监督。 |
   | **[!UICONTROL 开发人员]** | 可与代码和Git配合使用。 的Cloud Manager权限有限。 |

1. 要打开Cloud Manager，请登录到[Cloud Manager](https://my.cloudmanager.adobe.com/)，或转到[[!DNL Adobe Experience Cloud]](https://experience.adobe.com/) > **[!DNL Experience Manager]** > **[!UICONTROL Cloud Manager]**。 如果您的Adobe ID属于多个组织，请选择正确的组织。

>[!NOTE]
>
>Cloud Manager产品配置文件不提供对内容源的访问权限。 您还需要该环境的&#x200B;**[!UICONTROL AEM用户]**&#x200B;或&#x200B;**[!UICONTROL AEM管理员]**&#x200B;产品配置文件 — 请参阅[将用户分配给AEM产品配置文件](#assign-product-profile)。 仅具有默认Cloud Manager用户角色的用户可以打开环境，但无法获取程序级别的访问权限。

如果您登录但看不到项目或&#x200B;**[!UICONTROL Content AI配置]**&#x200B;选项卡，请要求管理员验证您分配的产品配置文件。 此外，请确认您在登录时选择了正确的组织。 AEM Managed Services使用与AEM as a Cloud Service不同的[!DNL Admin Console]产品上下文和设置。

要在初始登录期间创建程序，系统管理员必须首先具有&#x200B;**[!UICONTROL 业务负责人]**&#x200B;配置文件并登录到Cloud Manager。

有关更多信息，请参阅：

* [将团队成员分配给Cloud Manager产品配置文件](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-cloud-manager)
* [访问 Cloud Manager](https://experienceleague.adobe.com/zh-hans/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager)
* [AEM as a Cloud Service团队和产品配置文件](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/concepts/aem-cs-team-product-profiles)
* [添加用户和角色](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/users-and-roles)

## 将用户分配到 AEM 产品轮廓 {#assign-product-profile}

使用以下步骤，为用户授予特定环境中的 [!DNL Adobe Experience Manager] as a Cloud Service 访问权限。 请根据用户所需的访问权限分配相应的轮廓：

* **[!UICONTROL AEM 用户]** – 查看内容源。
* **[!UICONTROL AEM 管理员]** – 创建和编辑内容源。

>[!NOTE]
>
>用户必须属于 AEM 产品配置文件（如 **[!UICONTROL AEM 用户]**&#x200B;或 **[!UICONTROL AEM 管理员]**），才能访问 AEM。 仅拥有 Cloud Manager 访问权限并不足够。

要分配这些配置文件，您必须是具有 [!UICONTROL Business Owner] Cloud Manager 产品配置文件的系统管理员。 请提前准备好用户的姓名和电子邮件地址。

1. 在[Cloud Manager](https://my.cloudmanager.adobe.com/)中，导航到您的项目，并为目标环境选择&#x200B;**[!UICONTROL 管理访问权限]**。 系统将在新标签页中打开该环境对应的 [!DNL Adobe Admin Console]。
1. 为&#x200B;**作者**&#x200B;和&#x200B;**发布**&#x200B;层选择&#x200B;**[!UICONTROL AEM用户]**&#x200B;或&#x200B;**[!UICONTROL AEM管理员]**&#x200B;产品配置文件 — 例如，`AEM Administrators - author - Program 12345 - Environment 67890`和`AEM Administrators - publish - Program 12345 - Environment 67890`。
   * **[!UICONTROL AEM用户]** — 只读操作。
   * **[!UICONTROL AEM管理员]** — 写入操作，例如创建、编辑或删除内容源并触发客户获取。
1. 选择&#x200B;**[!UICONTROL 添加用户]**。
1. 输入用户的姓名和电子邮件地址，然后保存更改。 该用户将添加到产品轮廓中。

对于用户需要访问的每个环境（如开发、预发布或生产环境），请重复执行上述步骤。

>[!CAUTION]
>
>请勿编辑或删除名为 **[!UICONTROL AEM 管理员]**&#x200B;或 **[!UICONTROL AEM 用户]**&#x200B;的默认产品轮廓。 重命名 **[!UICONTROL AEM 管理员]**&#x200B;会导致所有分配到该轮廓的用户失去管理员权限。

### 验证分配结果 {#verify-assignment}

要验证分配是否成功：

1. 在 [!DNL Admin Console] 中，重新打开您分配的产品轮廓。
1. 确认该用户已显示在成员列表中。

如果您正在排查访问权限或令牌相关问题，请确认用户是直接添加到产品轮廓中的，而不仅仅是通过用户组获得权限。

## 步骤 1：打开“内容人工智能配置”选项卡 {#open-tab}

1. 登录 [Cloud Manager](https://my.cloudmanager.adobe.com/) 并选择您的程序。

   ![显示程序卡的 Cloud Manager 主页](../assets/content-ai-onboarding-step-1.png)

1. 在&#x200B;**[!UICONTROL 程序概览]**&#x200B;页面中，找到&#x200B;**[!UICONTROL 环境]**&#x200B;部分，然后选择要配置的环境。

   ![突出显示生产环境的程序概述](../assets/content-ai-onboarding-step-2.png)

1. 在环境详细信息页面中，选择 **[!UICONTROL 内容人工智能配置]**&#x200B;选项卡。

   ![突出显示“内容人工智能配置”选项卡的环境详细信息页面](../assets/content-ai-onboarding-step-3.png)

## 步骤 2：创建内容人工智能源 {#create-source}

内容源用于定义内容人工智能将要抓取和建立索引的网站。

1. 在 **[!UICONTROL 内容人工智能配置]**&#x200B;选项卡中，选择&#x200B;**[!UICONTROL 创建源]**。

   ![显示“创建源”按钮的“内容人工智能配置”选项卡](../assets/content-ai-onboarding-step-4.png)

1. 在&#x200B;**[!UICONTROL 创建/添加新的内容人工智能源]**&#x200B;对话框中，填写以下字段：

   | 字段 | 描述 |
   | --- | --- |
   | **[!UICONTROL 内容人工智能配置名称]** | 此源的唯一标识符（例如：`my-site-index`）。 创建后无法修改。 |
   | **[!UICONTROL 描述]** | *（可选）*&#x200B;内容源的简要说明。 |
   | **[!UICONTROL 网站地址]** | 要抓取的网站根 URL（例如：`https://www.example.com/`）。 |
   | **[!UICONTROL 排除 URL]** | *（可选）*&#x200B;抓取过程中需要跳过的 URL 模式。 |
   | **[!UICONTROL 刷新频率]** | 内容人工智能重新抓取该源的频率：每周、每天、每天 4 次、每 60 分钟或每 15 分钟。 |

   ![“创建内容人工智能源”对话框，其中名称和网站地址字段已填写，并突出显示“创建源”按钮](../assets/content-ai-onboarding-step-5-0.png)

   ![显示可用选项的刷新频率下拉列表](../assets/content-ai-onboarding-step-5-1.png)

1. 选择&#x200B;**[!UICONTROL 创建源]**。 获取会自动开始，源将进入&#x200B;**正在索引**&#x200B;状态。

   ![显示新创建的源处于“正在索引”状态的“内容源”列表](../assets/content-ai-onboarding-step-6.png)

## 步骤 3 - 重新运行获取 {#trigger-acquisition}

创建源时会自动运行获取，此后将按照&#x200B;**[!UICONTROL 刷新频率]**&#x200B;中设置的计划自动运行。 您也可以随时手动触发运行，例如，在发布新内容后立即重新编制索引。

1. 在源列表中，选择源旁边的&#x200B;**更多操作**（…）图标，然后选择&#x200B;**[!UICONTROL 触发获取]**。

   ![内容人工智能源列表，其中“更多操作”菜单已展开，并突出显示“触发获取”选项](../assets/content-ai-onboarding-step-7.png)

1. 在&#x200B;**[!UICONTROL 触发获取]**&#x200B;对话框中，检查源详细信息（包括&#x200B;**[!UICONTROL 内容源]**、**[!UICONTROL 上次运行时间]**&#x200B;和&#x200B;**[!UICONTROL 下次计划运行时间]**），然后选择&#x200B;**[!UICONTROL 触发]**。

   ![“触发获取”确认对话框](../assets/content-ai-onboarding-step-8.png)

## 步骤 4：监控索引状态 {#monitor-status}

内容获取开始后，源状态会实时更新。

| 状态 | 含义 |
| --- | --- |
| **新建** | 源刚刚创建，自动获取尚未开始。 此状态持续时间较短。 |
| **正在索引** | 内容获取正在进行中；系统正在抓取内容并建立索引。 |
| **可用** | 索引已完成，源已可用于搜索查询。 |

![显示“正在索引”状态的内容源列表](../assets/content-ai-onboarding-step-9.png)

![显示“可用”状态的内容源列表](../assets/content-ai-onboarding-step-10.png)

在搜索索引内容或测试 API 之前，请等待状态变为&#x200B;**可用**。

## 步骤 5：搜索已建立索引的内容 {#search-content}

当源状态变为&#x200B;**可用**&#x200B;后，您可以直接在 Cloud Manager 中执行搜索查询，以验证内容是否已正确建立索引。

1. 在源列表中，选择源旁边的&#x200B;**搜索**（放大镜）图标。

   ![“内容源”列表，其中可用源旁的搜索图标已高亮显示](../assets/content-ai-onboarding-step-13.png)

1. 在搜索框中输入查询内容。 搜索结果会显示匹配项列表，并包含匹配得分以及内容类型（例如 **PAGE** 或 **PDF**）。 选择某个结果后，会在右侧打开预览窗口。

   ![搜索面板，其中包含搜索查询、带匹配分数的匹配结果，以及用于显示排名第一结果的预览窗格](../assets/content-ai-onboarding-step-14.png)

## 修改或删除源 {#modify-source}

### 修改源 {#modify}

若要在创建后更新源配置：

1. 在源列表中，选择源旁边的&#x200B;**更多操作**（…）图标，然后选择&#x200B;**[!UICONTROL 编辑]**。

   ![内容源列表，其中“更多操作”菜单已展开，并突出显示“编辑”选项](../assets/content-ai-onboarding-step-11.png)

1. 在&#x200B;**[!UICONTROL 修改内容人工智能源]**&#x200B;对话框中，根据需要更新&#x200B;**[!UICONTROL 描述]**、**[!UICONTROL 网站地址]**、**[!UICONTROL 排除 URL]**&#x200B;或&#x200B;**[!UICONTROL 刷新频率]**。 **[!UICONTROL 内容人工智能配置名称]**&#x200B;为只读字段，无法修改。

   ![修改“内容人工智能源”对话框，其中可编辑字段已高亮显示](../assets/content-ai-onboarding-step-12.png)

1. 选择&#x200B;**[!UICONTROL 保存]**&#x200B;以应用更改。 源列表会更新并显示您所做的更改。

### 删除源 {#delete}

1. 在源列表中，选择源旁边的&#x200B;**更多操作**（…）图标，然后选择&#x200B;**[!UICONTROL 删除]**。

   >[!WARNING]
   >
   >删除源后无法恢复。 与该源关联的所有已建立索引的内容都会删除，并且无法再用于搜索查询。

删除后，该源将不再显示在列表中。

## 后续步骤 {#next-steps}

* [设置 Adobe Developer Console 项目](setup-adc-project.md)：创建调用 API 所需的 ADC 项目和凭据。
* [内容人工智能API 参考](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/)：使用语义搜索、全文搜索或混合搜索端点查询已建立索引的内容。

## 故障排除 {#troubleshooting}

* **源长时间停留在[!UICONTROL 正在索引]状态。** 从“（…）”菜单中重新触发内容获取。 如果第二次运行后状态仍未推进，请确认&#x200B;**[!UICONTROL 网站地址]**&#x200B;可从公共网络访问，并确保&#x200B;**[!UICONTROL 排除 URL]** 规则没有将所有页面全部过滤掉。
* **源在运行后又恢复为[!UICONTROL 新建]状态。** 爬虫无法从配置的根 URL 获取任何页面。 请确认该 URL 返回 `200 OK` 响应，并且网站未阻止自动化请求。
* 对状态为[!UICONTROL 可用]的源执行&#x200B;**[!UICONTROL 搜索]时未返回结果。** 索引已成功建立，但没有内容与查询条件匹配。 请尝试使用范围更广的查询条件，或检查已抓取的 URL 是否包含您期望的页面。
