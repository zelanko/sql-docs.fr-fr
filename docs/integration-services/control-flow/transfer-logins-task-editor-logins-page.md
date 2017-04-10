---
title: "&#201;diteur de t&#226;che de transfert de connexions (page Connexions) | Microsoft Docs"
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
  - "sql13.dts.designer.transferloginstask.logins.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de transfert de connexions"
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# &#201;diteur de t&#226;che de transfert de connexions (page Connexions)
  Utilisez la page **Connexions** de la boîte de dialogue **Éditeur de tâche de transfert de connexions** pour spécifier les propriétés de copie d'une ou plusieurs connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à une autre. Pour plus d'informations sur cette tâche, consultez [Transfer Logins Task](../../integration-services/control-flow/transfer-logins-task.md).  
  
> [!IMPORTANT]  
>  Lors de l'exécution de la tâche de transfert de connexions, les connexions sont créées sur le serveur de destination avec des mots de passe aléatoires qui sont désactivés. Pour utiliser ces connexions, un membre du rôle serveur fixe **sysadmin** doit changer les mots de passe et les activer. La connexion **sa** ne peut pas être transférée.  
  
## Options  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur de destination.  
  
 **LoginsToTransfer**  
 Sélectionnez les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à copier du serveur source au serveur de destination. Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**AllLogins**|Toutes les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le serveur source seront copiées sur le serveur de destination.|  
|**SelectedLogins**|Seules les connexions spécifiées dans **LoginsList** seront copiées sur le serveur de destination.|  
|**AllLoginsFromSelectedDatabases**|Toutes les connexions des bases de données spécifiées dans **DatabasesList** seront copiées sur le serveur de destination.|  
  
 **LoginsList**  
 Sélectionnez les connexions sur le serveur source à copier sur le serveur de destination. Cette option est disponible uniquement lorsque **SelectedLogins** est sélectionné pour **LoginsToTransfer**.  
  
 **DatabasesList**  
 Sélectionnez les bases de données du serveur source qui contiennent les connexions à copier sur le serveur de destination. Cette option est disponible uniquement lorsque **AllLoginsFromSelectedDatabases** est sélectionné pour **LoginsToTransfer**.  
  
 **IfObjectExists**  
 Sélectionnez la façon dont la tâche doit gérer les connexions de même nom que celles existant sur le serveur de destination.  
  
 Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**FailTask**|La tâche échoue si des connexions de même nom existent déjà sur le serveur de destination.|  
|**Remplacer**|La tâche remplace les connexions de même nom sur le serveur de destination.|  
|**Ignorer**|La tâche ignore les connexions de même nom qui existent sur le serveur de destination.|  
  
 **CopySids**  
 Déterminez si les identificateurs de sécurité associés aux connexions doivent être copiés sur le serveur de destination. **CopySids** doit prendre la valeur **True** si la tâche de transfert de connexions est utilisée en parallèle à la tâche de transfert de bases de données. Dans le cas contraire, les connexions copiées ne seront pas reconnues par la base de données transférée.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de connexions &#40;page Général&#41;](../../integration-services/control-flow/transfer-logins-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [Gestionnaire de connexions SMO](../../integration-services/connection-manager/smo-connection-manager.md)   
 [Mots de passe forts](../../relational-databases/security/strong-passwords.md)   
 [Considérations sur la sécurité pour une installation SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  