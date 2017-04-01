---
title: "&#201;diteur de t&#226;che de transfert de proc&#233;dures stock&#233;es de master (page G&#233;n&#233;ral) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferstoredprocedurestask.general.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de transfert de procédures stockées de master"
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# &#201;diteur de t&#226;che de transfert de proc&#233;dures stock&#233;es de master (page G&#233;n&#233;ral)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur de tâche de transfert de procédures stockées de master** pour nommer et décrire la tâche de transfert de procédures stockées de master. Pour plus d'informations sur cette tâche, consultez [Transfer Master Stored Procedures Task](../../integration-services/control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Cette tâche transfère seulement les procédures stockées définies par l’utilisateur appartenant à **dbo** d’une base de données **MASTER** sur le serveur source vers une base de données **MASTER** sur le serveur de destination. Les utilisateurs doivent disposer de l’autorisation Créer une procédure dans la base de données **MASTER** du serveur de destination ou être membres du rôle serveur fixe **sysadmin** sur le serveur de destination pour y créer des procédures stockées.  
  
## Options  
 **Nom**  
 Donnez un nom unique à la tâche de transfert de procédures stockées de master. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Entrez une description de la tâche de transfert de procédures stockées de master.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de procédures stockées de master &#40;page Procédures stockées&#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  