---
title: "Cr&#233;er et appliquer un instantan&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instantanés [réplication SQL Server], application"
  - "instantanés [réplication SQL Server], création."
ms.assetid: 631f48bf-50c9-4015-b9d8-8f1ad92d1ee2
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Cr&#233;er et appliquer un instantan&#233;
  Les instantanés sont générés par l'Agent d'instantané après la création d'une publication. Elles peuvent être générées :  
  
-   Immédiatement. Par défaut, un instantané pour une publication de fusion est généré immédiatement après la création de la publication dans l'Assistant Nouvelle publication.  
  
-   À une heure planifiée. Spécifiez une planification sur la **Agent de capture instantanée** page de l’Assistant Nouvelle Publication ou lors de l’utilisation des procédures stockées ou Replication Management Objects (RMO).  
  
-   Manuellement. Exécutez l'Agent d'instantané à partir de l'invite de commandes ou de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations sur l’exécution des agents, consultez [Concepts des exécutables de l’Agent réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) et [Démarrer et arrêter un Agent de réplication & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).  
  
 Pour la réplication de fusion, un instantané est généré à chaque exécution de l'Agent d'instantané. Pour la réplication transactionnelle, génération d’instantané dépend de la valeur de la propriété de publication **immediate_sync**. Si la propriété est définie avec la valeur TRUE (valeur par défaut lors de l'utilisation de l'Assistant Nouvelle publication), un instantané est généré à chaque exécution de l'Agent d'instantané, et peut être appliqué à un abonné à tout moment. Si la propriété est définie sur FALSE (la valeur par défaut lorsque vous utilisez **sp_addpublication**), l’instantané est généré uniquement si un nouvel abonnement a été ajouté depuis le dernier Agent de capture instantanée est exécuté ; Les abonnés doivent attendre l’Agent de capture instantanée à compléter avant de pouvoir se synchroniser.  
  
 Par défaut, lorsqu'ils sont générés, les instantanés sont enregistrés dans le dossier d'instantanés par défaut, situé sur le serveur de distribution. Vous pouvez également enregistrer les fichiers d'instantanés sur des supports amovibles, tels que les disques amovibles, les CD-ROM, ou tout emplacement autre que le dossier d'instantanés par défaut. De plus, vous pouvez compresser les fichiers afin de faciliter leur stockage et leur transfert, et exécuter des scripts avant ou après avoir appliqué l'instantané sur l'Abonné. Pour plus d’informations sur ces options, consultez la page [Options d’instantanés](../../relational-databases/replication/snapshot-options.md).  
  
 Si l'instantané est pour une publication de fusion utilisant des filtres paramétrés, il est créé à l'aide d'un processus en deux parties. D'abord, un instantané de schéma est créé contenant les scripts de réplication et le schéma des objets publiés, mais pas les données. Ensuite, chaque abonnement est initialisé avec un instantané comprenant les scripts et le schéma copiés à partir de l'instantané de schéma et des données appartenant à la partition de l'abonnement. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 Une fois l'instantané créé sur le serveur de publication et stocké dans un emplacement d'instantané par défaut ou de remplacement, l'instantané peut être transféré sur l'Abonné et appliqué. L'Agent de distribution (pour la réplication d'instantané ou transactionnelle) ou l'Agent de fusion (pour la réplication de fusion) transfère l'instantané et applique le schéma et les fichiers de données à la base de données d'abonnement sur l'Abonné pendant la synchronisation initiale. Par défaut, la synchronisation initiale se produit immédiatement après la création d'un abonnement si vous utilisez l'Assistant Nouvel abonnement. Ce comportement est contrôlé par la **initialiser lorsque** option sur le **initialiser les abonnements** page de l’Assistant. Lorsque les instantanés sont générés après l'initialisation d'un abonnement, ils ne sont pas appliqués à un abonné à moins qu'un abonnement ne soit marqué pour la réinitialisation. Pour plus d’informations, consultez [Réinitialiser les abonnements](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
 Une fois que l'Agent de distribution ou l'Agent de fusion a appliqué l'instantané initial, l'Agent propage les mises à jour suivantes et autres modifications de données. La distribution et l'application des instantanés n'affectent que les abonnés qui attendent un nouvel instantané ou un instantané initial. Les autres abonnés à cette publication (recevant déjà les insertions, mises à jour, suppressions ou autres modifications apportées aux données publiées) ne sont pas concernés.  
  
 Pour créer et appliquer l’instantané initial, [créer et appliquer la capture instantanée initiale](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
 Pour afficher ou modifier l'emplacement par défaut du dossier d'instantanés, consultez  
  
-   [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Specify the Default Snapshot Location &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)  
  
-   Programmation de la réplication et programmation RMO : [configurer la publication et la Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
## Voir aussi  
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Sécuriser le dossier d'instantané](../../relational-databases/replication/security/secure-the-snapshot-folder.md)   
 [sp_addpublication & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)  
  
  