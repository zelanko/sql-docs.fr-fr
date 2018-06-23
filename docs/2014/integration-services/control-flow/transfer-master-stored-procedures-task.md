---
title: Transfert de procédures stockées de master, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transfermasterspstask.f1
helpviewer_keywords:
- Transfer Master Stored Procedures task [Integration Services]
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fe704e638cb32ff397bf906c61593af6d07ba866
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153522"
---
# <a name="transfer-master-stored-procedures-task"></a>Tâche de transfert de procédures stockées de master
  La tâche de transfert de procédures stockées de master transfère une ou plusieurs procédures stockées définies par l’utilisateur entre les bases de données **master** sur des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour transférer une procédure stockée à partir de la base de données **master** , le propriétaire de la procédure doit être dbo.  
  
 La tâche de transfert de procédures stockées de master peut être configurée pour transférer toutes les procédures stockées ou seulement des procédures spécifiées. Cette tâche ne copie pas les procédures stockées système.  
  
 Les procédures stockées de master à transférer peuvent déjà exister à l'emplacement de destination. La tâche de transfert de procédures stockées de master peut être configurée pour traiter les procédures stockées existantes de différentes façons :  
  
-   Remplacer les procédures stockées existantes.  
  
-   Provoquer l'échec de la tâche lorsque des procédures stockées dupliquées existent.  
  
-   Ignorer les procédures stockées dupliquées.  
  
 À l'exécution, la tâche de transfert des procédures stockées de master se connecte aux serveurs source et destination en utilisant deux gestionnaires de connexions SMO. Les gestionnaires de connexions SMO sont configurés indépendamment de la tâche de transfert des procédures stockées de master, puis référencés dans celle-ci. Les gestionnaires de connexions SMO spécifient le serveur et le mode d'authentification à utiliser lors de l'accès au serveur. Pour plus d'informations, consultez [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
## <a name="transferring-stored-procedures-between-instances-of-sql-server"></a>Transfert de procédures stockées entre des instances de SQL Server  
 La tâche de transfert de procédures stockées de master prend en charge une source et une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="events"></a>Événements  
 La tâche génère un événement d'information qui indique le nombre de procédures stockées transférées et un événement d'avertissement lorsque qu'une procédure stockée est remplacée.  
  
 La tâche de transfert des procédures stockées de master n'indique pas les stades intermédiaires de l'avancement du transfert des connexions : elle signale la tâche comme réalisée à 0 % ou à 100 %.  
  
## <a name="execution-value"></a>Valeur d'exécution  
 La valeur de l’exécution, définie dans le `ExecutionValue` propriété de la tâche, renvoie le nombre de procédures stockées transférées. En affectant une variable définie par l’utilisateur pour le `ExecValueVariable` propriété de la tâche de procédures stockées de Master de transfert d’informations sur le transfert des procédures stockées peut être accessibles à d’autres objets dans le package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Entrées du journal  
 La tâche de transfert des procédures stockées comporte les entrées de journal personnalisées suivantes :  
  
-   TransferStoredProceduresTaskStartTransferringObjects Cette entrée du journal indique que le transfert a commencé. L'entrée du journal inclut l'heure de début.  
  
-   TransferSStoredProceduresTaskFinishedTransferringObjects Cette entrée du journal indique que le transfert est terminé. L'entrée du journal inclut l'heure de fin.  
  
 En outre, une entrée de journal pour le `OnInformation` signale le nombre de procédures stockées qui ont été transférés et une entrée de journal pour le `OnWarning` événement est écrit pour chaque procédure stockée à l’emplacement de destination est remplacé.  
  
## <a name="security-and-permissions"></a>Sécurité et autorisations  
 L’utilisateur doit avoir l’autorisation d’afficher la liste des procédures stockées dans la base de données **master** sur la source et doit être un membre du rôle serveur sysadmin ou disposer de l’autorisation de créer des procédures stockées dans la base de données **master** sur le serveur de destination.  
  
## <a name="configuration-of-the-transfer-master-stored-procedures-task"></a>Configuration de la tâche de transfert de procédures stockées de master  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Transférer l’éditeur de tâche de procédures stockées de Master &#40;Page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Transférer l’éditeur de tâche de procédures stockées de Master &#40;stockées Page procédures&#41;](../transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### <a name="configuring-the-transfer-master-stored-procedures-task-programmatically"></a>Configuration par programmation de la tâche de transfert de procédures stockées de master  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Transfert de tâche d’objets SQL Server](transfer-sql-server-objects-task.md)   
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  