---
title: "Propri&#233;t&#233;s de la publication, Instantan&#233; FTP et Internet | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1"
ms.assetid: 8e0198c3-5e4e-418c-9920-78ccbbfc1323
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Propri&#233;t&#233;s de la publication, Instantan&#233; FTP et Internet
  Cette page vous permet de :  
  
-   définir les propriétés d'envoi de l'instantané via FTP (File Transfer Protocol). Pour plus d’informations, consultez [instantanés via FTP Transfer](../../relational-databases/replication/transfer-snapshots-through-ftp.md). Pour utiliser FTP afin d'envoyer un instantané, vous devez définir un serveur FTP. Consultez la documentation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows pour plus d'informations.  
  
    > [!NOTE]  
    >  Les modifications des paramètres FTP nécessitent de générer un nouvel instantané.  
  
-   Définissez les propriétés de synchronisation Web de la réplication de fusion sur [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures qui permet de synchroniser les abonnements sur HTTPS (Secure Hypertext Transfer Protocol). Pour utiliser la synchronisation Web, vous devez configurer un serveur IIS ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services). Pour plus d’informations, voir [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## Options  
 **Accéder aux fichiers d'instantanés via FTP**  
 Sélectionnez **Autoriser les abonnés à télécharger des fichiers de capture instantanée à l’aide de FTP (File Transfer Protocol)**, et spécifiez **nom du serveur FTP**, **numéro de Port**, **chemin d’accès au dossier racine FTP**, **connexion**, et **mot de passe**, pour permettre aux abonnés d’utiliser FTP pour la remise d’un instantané.  
  
 Cette option permet aux abonnés d'utiliser FTP pour extraire les fichiers d'instantanés, mais elle ne les oblige pas à le faire. Si vous sélectionnez cette option, l'Assistant Nouvel abonnement amène par défaut les abonnés à extraire les fichiers d'instantanés via FTP. Pour modifier le paramètre, utilisez le **Propriétés d’un abonnement** boîte de dialogue. Si vous permettez aux abonnés d’accéder aux fichiers d’instantanés via FTP, spécifiez le dossier FTP comme emplacement des fichiers de capture instantanée sur le **instantané** page de le **Propriétés de la Publication** boîte de dialogue. Dans ce cas, l'Agent d'instantané met à jour automatiquement les fichiers du dossier FTP lorsqu'un nouvel instantané est généré. Si l'emplacement ne correspond pas au dossier FTP, vous devez mettre à jour les fichiers manuellement lorsqu'un nouvel instantané est généré. Pour plus d’informations, consultez [remettre un instantané via FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 **Synchronisation Web**  
 Réplication de fusion uniquement. Sélectionnez **Autoriser les abonnés à se synchroniser en se connectant à un serveur Web**, et spécifiez une adresse de serveur Web pour permettre aux abonnés d’utiliser la synchronisation Web. Le serveur Web doit utiliser SSL (Secure Sockets Layer), et l'adresse Web doit être complètement qualifiée (https://server.domain.com/synchronize, par exemple). Pour plus d'informations, voir [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md).  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Créer et appliquer l'instantané initial](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  