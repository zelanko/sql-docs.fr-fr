---
title: Transfert de l’éditeur de tâche de connexions (Page connexions) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 131c74b2637fb0181e55838b1430fb0b33a14d3f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926812"
---
# <a name="transfer-logins-task-editor-logins-page"></a>Éditeur de tâche de transfert de connexions (page Connexions)
  Utilisez la page **Connexions** de la boîte de dialogue **Éditeur de tâche de transfert de connexions** pour spécifier les propriétés de copie d'une ou plusieurs connexions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] d'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à une autre. Pour plus d'informations sur cette tâche, consultez [Transfer Logins Task](control-flow/transfer-logins-task.md).  
  
> [!IMPORTANT]  
>  Lors de l'exécution de la tâche de transfert de connexions, les connexions sont créées sur le serveur de destination avec des mots de passe aléatoires qui sont désactivés. Pour utiliser ces connexions, un membre du rôle serveur fixe **sysadmin** doit changer les mots de passe et les activer. La connexion **sa** ne peut pas être transférée.  
  
## <a name="options"></a>Options  
 **SourceConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur source.  
  
 **DestinationConnection**  
 Sélectionnez un gestionnaire de connexions SMO dans la liste, ou cliquez sur **\<Nouvelle connexion...>** pour créer une connexion au serveur de destination.  
  
 **LoginsToTransfer**  
 Sélectionnez les connexions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à copier du serveur source au serveur de destination. Cette propriété dispose des options répertoriées dans le tableau suivant :  
  
|Value|Description|  
|-----------|-----------------|  
|**AllLogins**|Toutes les connexions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur le serveur source seront copiées sur le serveur de destination.|  
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
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Éditeur de tâche de transfert de connexions &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page Expressions](expressions/expressions-page.md)   
 [Gestionnaire de connexions SMO](connection-manager/smo-connection-manager.md)   
 [Mots de passe forts](../relational-databases/security/strong-passwords.md)   
 [Considérations sur la sécurité pour une installation SQL Server](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
