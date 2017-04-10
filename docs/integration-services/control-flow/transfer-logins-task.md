---
title: "T&#226;che de transfert de connexions | Microsoft Docs"
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
  - "sql13.dts.designer.transferloginstask.f1"
helpviewer_keywords: 
  - "tâche de transfert de connexions [Integration Services]"
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# T&#226;che de transfert de connexions
  La tâche de transfert de connexions transfère une ou plusieurs connexions entre des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Transférer des connexions entre des instances de SQL Server  
 La tâche de transfert de connexions prend en charge une source et une destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Événements  
 La tâche génère un événement d'information qui indique le nombre de connexions transférées et un événement d'avertissement quand une connexion est remplacée.  
  
 La tâche de transfert des connexions n'indique pas les stades intermédiaires de l'avancement du transfert des connexions : elle signale la tâche comme réalisée à 0 % ou à 100 %.  
  
## Valeur d'exécution  
 La valeur d’exécution, définie dans la propriété **ExecutionValue** de la tâche, retourne le nombre de connexions transférées. En affectant une variable définie par l’utilisateur à la propriété **ExecValueVariable** de la tâche de transfert de connexions, les informations sur le transfert des connexions peuvent être rendues disponibles pour d’autres objets du package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) et [Utiliser des variables dans des packages](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Entrées du journal  
 La tâche de transfert des connexions comporte les entrées du journal personnalisées suivantes :  
  
-   TransferLoginsTaskStarTransferringObjects   Cette entrée du journal indique que le transfert a commencé. L'entrée du journal inclut l'heure de début.  
  
-   TransferLoginsTaskFinishedTransferringObjects   Cette entrée du journal indique que le transfert est terminé. L'entrée du journal inclut l'heure de fin.  
  
 De plus, une entrée de journal pour l’événement **OnInformation** indique le nombre de connexions qui ont été transférées, et une entrée de journal pour l’événement **OnWarning** est générée pour chaque connexion remplacée à l’emplacement de destination.  
  
## Sécurité et autorisations  
 Pour parcourir les connexions sur le serveur source et créer des connexions sur le serveur de destination, l'utilisateur doit être un membre du rôle de serveur sysadmin sur les deux serveurs.  
  
## Configuration de la tâche de transfert des connexions  
 La tâche de transfert de connexions peut être configurée pour transférer toutes les connexions, seulement les connexions spécifiées ou toutes les connexions ayant accès à une base de données spécifiée. La connexion sa ne peut pas être transférée. La connexion sa peut être renommée ; cependant, la connexion sa renommée ne peut pas être transférée non plus.  
  
 Vous pouvez également indiquer si la tâche copie les identificateurs de sécurité (SID) associés aux connexions. Si la tâche de transfert des connexions est utilisée en conjonction avec la tâche de transfert des bases de données, les SID doivent être copiés à l'emplacement de destination ; si ce n'est pas le cas, les connexions transférées ne sont pas reconnues par la base de données de destination.  
  
 À l'emplacement de destination, les connexions transférées sont désactivées et des mots de passe aléatoires leur sont affectés. Un membre du rôle sysadmin sur le serveur de destination doit modifier les mots de passe et activer les connexions avant que ces dernières puissent être utilisées.  
  
 Les connexions à transférer peuvent déjà exister à l'emplacement de destination. La tâche de transfert des connexions peut être configurée pour traiter les connexions existantes de différentes manières :  
  
-   Remplacer les connexions existantes  
  
-   Provoquer l'échec de la tâche lorsque des connexions dupliquées existent.  
  
-   Ignorer les connexions dupliquées  
  
 À l'exécution, la tâche de transfert des connexions se connecte aux serveurs source et destination en utilisant deux gestionnaires de connexions SMO. Les gestionnaires de connexions SMO sont configurés indépendamment de la tâche de transfert des connexions, puis référencés dans celle-ci. Les gestionnaires de connexions SMO spécifient le serveur et le mode d'authentification à utiliser lors de l'accès au serveur. Pour plus d'informations, consultez [SMO Connection Manager](../../integration-services/connection-manager/smo-connection-manager.md).  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de transfert de connexions &#40;page Général&#41;](../../integration-services/control-flow/transfer-logins-task-editor-general-page.md)  
  
-   [Éditeur de tâche de transfert de connexions &#40;page Connexions&#41;](../../integration-services/control-flow/transfer-logins-task-editor-logins-page.md)  
  
-   [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Configuration de la tâche de transfert des connexions par programme  
 Pour plus d'informations sur la définition par programme de ces propriétés, cliquez sur la rubrique suivante :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  