---
title: "&#201;diteur de destination SQL (page Gestionnaire de connexions) | Microsoft Docs"
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
  - "sql13.dts.designer.sqlserverdestadapter.connection.f1"
helpviewer_keywords: 
  - "Éditeur de destination SQL Server"
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# &#201;diteur de destination SQL (page Gestionnaire de connexions)
  Utilisez la page **Gestionnaire de connexions** de la boîte de dialogue **Éditeur de destination SQL** pour spécifier des informations sur la source de données et afficher un aperçu des résultats. La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge les données dans des tables ou des vues, dans une base de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour en savoir plus sur la destination pour SQL Server, consultez [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md).  
  
## Options  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou créez une connexion en cliquant sur **Nouvelle**.  
  
 **Nouveau**  
 Crée une connexion en utilisant la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB**.  
  
 **Utiliser une table ou une vue**  
 Sélectionnez une table ou une vue existante dans la liste, ou créez une connexion en cliquant sur **Nouvelle**.  
  
 **Nouveau**  
 Utilisez la boîte de dialogue **Créer une table** pour créer une table.  
  
> [!NOTE]  
>  Quand vous cliquez sur **Nouvelle**, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] génère une instruction CREATE TABLE par défaut, basée sur la source de données connectée. Cette instruction CREATE TABLE par défaut n'inclut pas l'attribut FILESTREAM, même si la table source inclut une colonne dans laquelle l'attribut FILESTREAM est déclaré. Pour exécuter un composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] avec l'attribut FILESTREAM, implémentez d'abord le stockage FILESTREAM sur la base de données de destination. Ajoutez ensuite l’attribut FILESTREAM à l’instruction CREATE TABLE dans la boîte de dialogue **Créer une table**. Pour plus d’informations, consultez [Données blob &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Aperçu**  
 Affichez un aperçu des résultats à l’aide de la boîte de dialogue **Visualiser les résultats de la requête**. L'aperçu peut afficher jusqu'à 200 lignes.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de destination SQL &#40;page Mappages&#41;](../../integration-services/data-flow/sql-destination-editor-mappings-page.md)   
 [Éditeur de destination SQL &#40;page Avancé&#41;](../../integration-services/data-flow/sql-destination-editor-advanced-page.md)   
 [Charger des données en masse à l'aide de la destination SQL Server](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  