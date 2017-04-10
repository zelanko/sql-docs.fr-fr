---
title: "Ex&#233;cuter des scripts avant et apr&#232;s l&#39;application de l&#39;instantan&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instantanés [réplication SQL Server], scripts"
  - "scripts [réplication SQL Server], instantanés"
  - "réplication d’instantané [SQL Server], scripts"
  - "scripts [réplication SQL Server]"
ms.assetid: 9a6872c2-9bed-477f-9d2f-332d640edcf2
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Ex&#233;cuter des scripts avant et apr&#232;s l&#39;application de l&#39;instantan&#233;
  Vous pouvez spécifier les scripts à exécuter sur l'Abonné avant ou après l'application de l'instantané. Les scripts peuvent être utilisés à diverses fins, par exemple pour créer des connexions et des schémas (propriétaires d'objets) sur chaque Abonné.  
  
 Vous spécifiez un emplacement de fichier pour chaque script et l'Agent d'instantané copie les fichiers de script dans le dossier d'instantanés actif à chaque traitement d'instantané. L'Agent de distribution ou l'Agent de fusion exécute le script antérieur à l'instantané avant tout autre script d'objet répliqué lors de l'application d'un instantané. Il exécute le script postérieur à l'instantané après l'application de tous les autres scripts et données d'objets répliqués. Au terme de l'application de l'instantané et de l'exécution correcte des fichiers de script, ces derniers sont supprimés du répertoire de travail sur l'Abonné.  
  
 Le script est exécuté en lançant le **sqlcmd** utilitaire. Avant de déployer un script, exécutez-le avec **sqlcmd** pour vous assurer qu’il s’exécute comme prévu. Le contenu des scripts exécutés avant et après l'application de l'instantané doit être renouvelable. Si, par exemple, vous créez une table dans le script, commencez par vérifier qu'elle existe et, dans l'affirmative, procédez de la façon appropriée. Le script doit être renouvelable car, s'il est nécessaire de réinitialiser un abonnement dont le script a déjà été appliqué, ce dernier sera réexécuté lors de l'application du nouvel instantané au cours de la réinitialisation.  
  
 Si vous compressez le fichier d'instantanés (en le convertissant au format de fichier [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB), les scripts sont également compressés et placés dans le fichier CAB. Après le transfert du fichier d'instantanés compressé vers l'Abonné et sa décompression dans un répertoire de travail sur l'Abonné, tout script indiqué comme script antérieur à l'instantané est exécuté. De même, tous les scripts postérieurs à l'instantané sont décompressés et exécutés sur l'Abonné lors de l'étape finale de l'application de l'instantané.  
  
 **Pour exécuter des scripts avant et après l'application de l'instantané**  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [How to: Execute Scripts Before and After a Snapshot is Applied \(SQL Server Management Studio\)](../../relational-databases/replication/execute scripts before and after a snapshot is applied.md)  
  
-   Réplication [!INCLUDE[tsql](../../includes/tsql-md.md)] programming : [configurer les propriétés d’instantané & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## Voir aussi  
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Options d'instantané](../../relational-databases/replication/snapshot-options.md)  
  
  