---
title: "&#201;diteur de t&#226;che de transfert de proc&#233;dures stock&#233;es de master (page Proc&#233;dures stock&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferstoredprocedurestask.storedprocedures.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de transfert de procédures stockées de master"
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
caps.latest.revision: 20
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 20
---
# &#201;diteur de t&#226;che de transfert de proc&#233;dures stock&#233;es de master (page Proc&#233;dures stock&#233;es)
  La page **Procédures stockées** de la boîte de dialogue **Éditeur de tâche de transfert de procédures stockées de master** permet de spécifier les propriétés de copie d’une ou plusieurs procédures stockées définies par l’utilisateur de la base de données **MASTER** d’une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une base de données **MASTER** d’une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations sur cette tâche, consultez [Transfer Master Stored Procedures Task](../../integration-services/control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  Cette tâche transfère uniquement les procédures stockées définies par l’utilisateur appartenant à **dbo** d’une base de données **MASTER** du serveur source vers une base de données **MASTER** du serveur de destination. Les utilisateurs doivent disposer de l’autorisation Créer une procédure dans la base de données **MASTER** du serveur de destination ou être membres du rôle serveur fixe **sysadmin** sur le serveur de destination pour y créer des procédures stockées.  
  
## Options  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur de destination.  
  
 **IfObjectExists**  
 Sélectionnez la façon dont la tâche doit traiter les procédures stockées définies par l’utilisateur qui existent déjà sous le même nom dans la base de données **MASTER** du serveur de destination.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**FailTask**|La tâche échoue si des procédures stockées du même nom existent déjà dans la base de données **MASTER** du serveur de destination.|  
|**Remplacer**|La tâche remplace les procédures stockées du même nom dans la base de données **MASTER** du serveur de destination.|  
|**Ignorer**|La tâche ignore les procédures stockées qui existent sous le même nom dans la base de données **MASTER** du serveur de destination.|  
  
 **TransferAllStoredProcedures**  
 Indiquez si toutes les procédures stockées définies par l’utilisateur dans la base de données **MASTER** sur le serveur source doivent être copiées sur le serveur de destination.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**True**|Copie toutes les procédures stockées définies par l’utilisateur dans la base de données **MASTER**.|  
|**False**|Copie uniquement les procédures stockées spécifiées.|  
  
 **StoredProceduresList**  
 Sélectionnez les procédures stockées définies par l’utilisateur dans la base de données **MASTER** du serveur source qui doivent être copiées dans la base de données **MASTER** de destination. Cette option est disponible uniquement lorsque **TransferAllStoredProcedures** a la valeur **False**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de procédures stockées de master &#40;page Général&#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Gestionnaire de connexions SMO](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  