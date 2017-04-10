---
title: "activer un serveur de publication distant sur un serveur de distribution (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "serveurs de distribution distants [réplication SQL Server]"
  - "Serveur de publications [réplication SQL Server]"
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# activer un serveur de publication distant sur un serveur de distribution (SQL Server Management Studio)
  Activer un serveur de publication à utiliser un serveur de distribution distant sur le **éditeurs** page. Cette page est disponible dans l’Assistant Configuration de la Distribution et la **des propriétés de serveur de distribution - \< serveur de distribution>** boîte de dialogue. Pour plus d’informations sur l’utilisation de l’Assistant et accéder à la boîte de dialogue, consultez [configurer la publication et la Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md) et [Afficher et de modifier le serveur de distribution et de propriétés de l’éditeur](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### Pour activer un serveur de publication dans l'Assistant Configuration de distribution  
  
1.  Sur le **éditeurs** page de l’Assistant Configuration de Distribution, cliquez sur **Ajouter**.  
  
2.  Cliquez sur **Ajouter le serveur de publication SQL Server**. Pour plus d’informations sur l’activation d’un serveur de publication Oracle utiliser un serveur de distribution, consultez [créer une Publication à partir d’une base de données Oracle](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez les informations de connexion pour le serveur de publication qui utilisent le serveur de distribution distant, puis cliquez sur **Connect**.  
  
4.  Sur le **mot de passe de serveur de distribution** page, dans le **mot de passe** et **Confirmer le mot de passe** zones de texte, spécifiez un mot de passe fort pour le **distributor_admin** compte, la réplication utilise pour se connecter à partir du serveur de publication au serveur de distribution pour effectuer des tâches administratives.  
  
5.  Pour afficher et modifier les paramètres d’un serveur de publication, cliquez sur le bouton des propriétés (**...**).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour activer un serveur de publication dans la boîte de dialogue Propriétés du serveur de distribution  
  
1.  Sur le **éditeurs** page de le **Propriétés du serveur de distribution - \< serveur de distribution>** boîte de dialogue, cliquez sur **Ajouter**.  
  
2.  Cliquez sur **Ajouter le serveur de publication SQL Server**. Pour plus d’informations sur l’activation d’un serveur de publication Oracle utiliser un serveur de distribution, consultez [créer une Publication à partir d’une base de données Oracle](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
3.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez les informations de connexion pour le serveur de publication qui utilisent le serveur de distribution distant, puis cliquez sur **Connect**.  
  
4.  Sur le **éditeurs** page, dans le **mot de passe** et **Confirmer le mot de passe** zones de texte, spécifiez un mot de passe fort pour le **distributor_admin** compte, la réplication utilise pour se connecter à partir du serveur de publication au serveur de distribution pour effectuer des tâches administratives.  
  
5.  Pour afficher et modifier les paramètres d’un serveur de publication, cliquez sur le bouton des propriétés (**...**).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Voir aussi  
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [Protéger le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  