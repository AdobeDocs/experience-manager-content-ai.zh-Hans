---
title: 为AEM Content AI设置Adobe Developer Console项目
description: 了解如何使用服务器到服务器或API密钥身份验证来设置Adobe Developer Console项目并验证AEM Content AI服务的API调用。
topic: Configuration
role: Developer, Admin
level: Beginner
solution: Experience Manager
keywords: AEM Content AI， Adobe Developer Console，身份验证，服务器到服务器， API密钥，访问令牌
source-git-commit: 445aeafe64eb8a68d0770c1f1afb54d68e0b054f
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 2%

---


# 设置Adobe Developer Console项目 {#configure-adc-project}

要调用AEM Content AI服务API，您需要由Adobe Developer Console (ADC)项目颁发的凭据。 此页面将指导您创建项目、选择身份验证方法以及生成随每个API请求一起包含的凭据。

转到[Adobe Developer Console](https://developer.adobe.com/console/)以开始您的组织。

## 先决条件 {#prerequisites}

在开始之前，请确保满足以下条件：

* 您有权访问贵组织的[Adobe Developer Console](https://developer.adobe.com/console/)。
* 您在&#x200B;**Adobe Admin Console**&#x200B;中的AEM Content AI服务产品配置文件中被添加为&#x200B;**开发人员**。 如果没有此角色，**[!UICONTROL AEM Content AI Services]** API卡显示为已禁用，**[!UICONTROL 服务器到服务器]**&#x200B;身份验证选项为隐藏。
* 您知道要选择的产品配置文件的项目和环境编号（例如，`AEM User - publish - Program 12345 - Environment 67890`）。

## 选择身份验证方法 {#choose-auth}

AEM Content AI服务支持两种身份验证方法。 选择与您的集成匹配的：

| 方法 | 最适合 |
| --- | --- |
| [服务器到服务器](#s2s-auth) | 无需用户交互即可调用API的后端服务。 返回短期访问令牌。 |
| [API密钥](#api-key-auth) | 直接调用API的基于客户端或浏览器的集成。 返回范围设为允许域的长寿命密钥。 |

## 服务器到服务器身份验证 {#s2s-auth}

1. 选择&#x200B;**[!UICONTROL API和服务]**，然后选择&#x200B;**[!UICONTROL API]**。

   显示API和服务的![Developer Console](../assets/e2e-env-setup-28.png)

1. 按&#x200B;**AEM Content AI Services**&#x200B;筛选，然后选择&#x200B;**[!UICONTROL 创建项目]**&#x200B;以启动新项目，或者如果要将服务添加到现有项目，请选择&#x200B;**[!UICONTROL 添加API]**。

   >[!NOTE]
   >
   >如果API卡因“需要许可证”消息而被禁用，则您的AEM as a Cloud Service环境可能无法实现现代化。 请参阅[AEM as a Cloud Service环境的现代化](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/openapis/setup#modernization-of-aem-as-a-cloud-service-environment)。

1. 在&#x200B;**[!UICONTROL 配置API]**&#x200B;对话框中，选择&#x200B;**[!UICONTROL 服务器到服务器]**&#x200B;身份验证。

   ![选择了服务器到服务器的“配置API”对话框](../assets/e2e-env-setup-29.png)

   >[!TIP]
   >
   >如果服务器到服务器选项不可用，则设置集成的用户将不会作为开发人员添加到产品配置文件中。 请参阅[启用服务器到服务器身份验证](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)。

1. 如果需要，请重命名凭据。 选择&#x200B;**[!UICONTROL 下一步]**。

   ![Adobe Developer Console步骤，用于在选择“下一步”之前重命名新的服务器到服务器凭据](../assets/e2e-env-setup-30.png)

1. 选择&#x200B;**[!UICONTROL AEM用户 — 发布 — 程序XXX — 环境XXX]**&#x200B;和/或&#x200B;**[!UICONTROL AEM用户 — 作者 — 程序XXX — 环境XXX]**&#x200B;产品配置文件，然后选择&#x200B;**[!UICONTROL 保存]**。

   ![产品配置文件选取器显示AEM用户发布和作者的Target项目和环境配置文件](../assets/e2e-env-setup-31.png)

1. 审查API和身份验证配置。

   ![概述所选API、身份验证类型和凭据名称的审阅屏幕](../assets/e2e-env-setup-33.png)

   ![查看屏幕详细信息，显示已分配的凭据的产品配置文件](../assets/e2e-env-setup-34.png)

### 生成访问令牌 {#generate-token}

1. 在您的ADC项目中，转到&#x200B;**[!UICONTROL 凭据]**&#x200B;并选择&#x200B;**[!UICONTROL 生成访问令牌]**。

   突出显示“生成访问令牌”按钮的![凭据页面](../assets/e2e-env-setup-32.png)

1. 在每个API请求的`Authorization`标头中包含令牌：

   ```http
   Authorization: Bearer YOUR_ACCESS_TOKEN
   ```

   >[!WARNING]
   >
   >安全地存储令牌。 它将会过期，必须定期重新生成。

## API密钥身份验证 {#api-key-auth}

1. 将AEM Content AI Services API添加到项目时，请在&#x200B;**[!UICONTROL 选择身份验证类型]**&#x200B;对话框中选择&#x200B;**[!UICONTROL API密钥]**。

   ![选择API密钥身份验证类型](../assets/onboarding-api-key-01.png)

1. 确认API密钥凭据。

   ![添加API密钥凭据](../assets/onboarding-api-key-02.png)

1. 要限制哪些源可以使用键，请配置允许的域。

   ![配置允许的域](../assets/onboarding-api-key-03.png)

1. 您的API密钥（客户端ID）出现在&#x200B;**[!UICONTROL 连接的凭据]**&#x200B;下。 选择&#x200B;**[!UICONTROL 复制]**。

   ![从连接的凭据复制API密钥](../assets/onboarding-api-key-04.png)

1. 在每个API请求中包含密钥：

   ```http
   x-api-key: YOUR_API_KEY
   ```

   您的项目现已准备就绪。 在对AEM Content AI服务的每个请求中都使用密钥。

## 后续步骤 {#next-steps}

* [控制您的内容源](contentsources.md) — 在Cloud Manager中配置内容源并触发客户获取。
* [内容人工智能API引用](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/contentai/) — 使用您的访问令牌或API密钥查询已索引的内容。
