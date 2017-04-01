---
title: "Propri&#233;t&#233;s de la publication, Instantan&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.snapshotformat.f1"
ms.assetid: 8e9133b1-fc37-4a85-8a7c-d5eaf172fbef
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# Propri&#233;t&#233;s de la publication, Instantan&#233;
  Le **instantané** page de le **Propriétés de la Publication** boîte de dialogue vous permet de définir le format d’instantané, emplacement de dossier de capture instantanée et les scripts à exécuter avant et après l’application de l’instantané. Le dossier d'instantanés doit être défini comme partage et disposer des autorisations suffisantes pour les agents qui lisent et écrivent des fichiers dans le dossier. Pour plus d’informations sur la sécurisation du dossier de manière appropriée, consultez [sécuriser le dossier de capture instantanée](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
> [!NOTE]  
>  Les modifications nécessitent un nouvel instantané pour la publication. Pour plus d’informations, consultez [Publication de modification et les propriétés de l’Article](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## Options  
 **Format d'instantané**  
 Sélectionnez le mode natif ou le mode caractère pour le format d'instantané.  
  
-   Sélectionnez **SQL Server natif - tous les abonnés doivent être des serveurs exécutant SQL Server** si tous les abonnés sont des instances de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autre que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Le format natif d'instantané fournit les meilleures performances.  
  
-   Sélectionnez **caractère - obligatoire si un serveur de publication ou un abonné n’exécute pas SQL Server** Si des abonnés exécutent [!INCLUDE[ssEW](../../includes/ssew-md.md)] ou non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés.  
  
 **Emplacement des fichiers d'instantané**  
 Sélectionnez l'emplacement des fichiers d'instantané. Vous pouvez les stocker dans l'emplacement par défaut et dans un emplacement différent, ou seulement dans un emplacement différent. Les fichiers stockés dans un emplacement différent peuvent être compressés.  
  
-   Sélectionnez **placer les fichiers dans le dossier par défaut** à utiliser le dossier de capture instantanée par défaut pour le serveur de publication. L’emplacement de dossier de capture instantanée est en lecture seule dans cette boîte de dialogue, car il ne peut être modifié pour le serveur de publication dans le **des propriétés de serveur de distribution** boîte de dialogue. Pour plus d’informations, consultez [spécifier l’emplacement par défaut des instantanés & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
-   Sélectionnez **placer les fichiers dans le dossier suivant** pour spécifier un autre emplacement à la place ou en plus, l’emplacement par défaut. Entrez un chemin d’accès dans la zone de texte ou cliquez sur **Parcourir** et accédez à l’emplacement. Sélectionnez **Compresser les fichiers d’instantanés dans ce dossier** pour compresser les fichiers dans l’autre emplacement. L'emplacement secondaire peut se trouver sur un autre serveur, un lecteur réseau ou un support amovible (tel qu'un CD-ROM ou un disque amovible). Pour plus d'informations, consultez [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md) et [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md).  
  
 **Exécuter des scripts supplémentaires**  
 Définissez les scripts à exécuter avant et après l'application de l'instantané au niveau de l'Abonné. Les scripts ne peut pas être spécifiés si **format d’instantané** est **caractères**.  
  
 Les scripts sont facultatifs, mais ils fournissent une méthode simple pour exécuter des commandes et appliquer des modifications administratives au niveau des abonnés. Pour plus d’informations sur l’exécution de scripts, consultez [exécuter des Scripts avant et après l’application de capture instantanée](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Entrez un chemin d’accès dans la **exécuter ce script avant l’application de l’instantané** zone de texte ou cliquez sur **Parcourir** pour spécifier un emplacement pour le script.  
  
-   Entrez un chemin d’accès dans la **exécuter ce script après l’application de l’instantané** zone de texte ou cliquez sur **Parcourir** pour spécifier un emplacement pour le script.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Créer et appliquer l'instantané initial](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  