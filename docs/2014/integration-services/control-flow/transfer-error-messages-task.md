---
title: Transférer les messages d’erreur, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.f1
helpviewer_keywords:
- Transfer Error Messages task [Integration Services]
ms.assetid: da702289-035a-4d14-bd74-04461fbfee1b
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2d7a40c86c0dba2a4b2db08305f7fea379a97b1f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201849"
---
# <a name="transfer-error-messages-task"></a>Tâche de transfert de messages d'erreur
  La tâche de transfert de messages d’erreur transfère un ou plusieurs messages d’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définis par l’utilisateur entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les messages définis par l'utilisateur sont des messages avec un identificateur supérieur ou égal à 50 000. Les messages dont l'identificateur est inférieur à 50 000 sont des messages d'erreur système qui ne peuvent pas être transférés à l'aide de la tâche de transfert de messages d'erreur.  
  
 La tâche de transfert de messages d'erreur peut être configurée pour transférer tous les messages d'erreur ou uniquement les messages d'erreur spécifiés. Les messages d'erreur définis par l'utilisateur peuvent être disponibles en différentes langues et la tâche peut être configurée pour ne transférer que les messages dans des langues sélectionnées. Une version us_english du message qui utilise la page de codes 1033 doit exister sur le serveur de destination avant que vous ne puissiez transférer d'autres versions linguistiques du message vers ce serveur.  
  
 La table sysmessages dans la base de données master contient tous les messages d'erreur (système et définis par l'utilisateur) utilisés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Les messages définis par l'utilisateur à transférer peuvent déjà exister à l'emplacement de destination. Un message d'erreur est défini comme message d'erreur dupliqué si l'identificateur et la langue sont identiques. La tâche de transfert de messages d'erreur peut être configurée pour traiter les messages d'erreur existants de différentes manières :  
  
-   Remplacer les messages d'erreur existants.  
  
-   Provoquer l'échec de la tâche lorsque des messages dupliqués existent.  
  
-   Ignorer les messages d'erreur dupliqués.  
  
 À l'exécution, la tâche de transfert de messages d'erreur se connecte aux serveurs source et destination en utilisant un ou deux gestionnaires de connexions SMO. Le gestionnaire de connexions SMO est configuré indépendamment de la tâche de transfert de messages d'erreur, puis il est référencé dans celle-ci. Le gestionnaire de connexions SMO spécifie le serveur et le mode d'authentification à utiliser lors de l'accès au serveur. Pour plus d'informations, consultez [SMO Connection Manager](../connection-manager/smo-connection-manager.md).  
  
 La tâche de transfert de messages d’erreur prend en charge une source et une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Chacune des versions peut être utilisée indifféremment comme source ou comme destination.  
  
## <a name="events"></a>Événements  
 La tâche génère un événement d'information qui indique le nombre de messages d'erreur transférés.  
  
 La tâche de transfert de messages d'erreur n'indique pas les stades intermédiaires de l'avancement du transfert des messages d'erreur : elle signale la tâche comme réalisée à 0 % ou à 100 %.  
  
## <a name="execution-value"></a>Valeur d'exécution  
 La valeur de l’exécution, définie dans le `ExecutionValue` propriété de la tâche, retourne le nombre de messages d’erreur qui ont été transférés. En affectant une variable définie par l’utilisateur à la `ExecValueVariable` propriété de la tâche Message d’erreur de transfert, les informations sur le transfert de message d’erreur peut être rendue disponible aux autres objets dans le package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../use-variables-in-packages.md).  
  
## <a name="log-entries"></a>Entrées du journal  
 La tâche de transfert de messages d'erreur comporte les entrées de journal personnalisées suivantes :  
  
-   TransferErrorMessagesTaskStartTransferringObjects    Cette entrée du journal indique que le transfert a commencé. L'entrée du journal inclut l'heure de début.  
  
-   TransferErrorMessagesTaskFinishedTransferringObjects   Cette entrée du journal indique que le transfert est terminé. L'entrée du journal inclut l'heure de fin.  
  
 En outre, une entrée de journal pour le `OnInformation` événement signale le nombre de messages d’erreur qui ont été transférés et une entrée de journal pour le `OnWarning event` est écrit pour chaque message d’erreur à l’emplacement de destination est remplacé.  
  
## <a name="security-and-permissions"></a>Sécurité et autorisations  
 Pour créer de nouveaux messages d'erreur, l'utilisateur qui exécute le package doit être un membre du rôle de serveur sysadmin ou serveradmin sur le serveur de destination.  
  
## <a name="configuration-of-the-transfer-error-messages-task"></a>Configuration de la tâche de transfert de messages d'erreur  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de Messages d’erreur transfert &#40;Page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche de Messages d’erreur transfert &#40;Page des Messages&#41;](../transfer-error-messages-task-editor-messages-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferErrorMessagesTask.TransferErrorMessagesTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  
