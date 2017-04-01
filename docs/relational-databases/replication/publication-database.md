---
title: "Base de donn&#233;es de publication | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.publicationdatabase.f1"
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Base de donn&#233;es de publication
  La base de données de publication est la base de données située sur le serveur de publication, qui sert de source aux données et aux objets de base de données à répliquer. Chaque base de données de publication mise en œuvre lors de la réplication doit obligatoirement être activée. La base de données est activée lorsqu'un membre du rôle serveur fixe **sysadmin** :  
  
-   crée une publication relative à la base de données par le biais de l'Assistant Nouvelle publication ;  
  
-   sélectionne la base de données dans la boîte de dialogue **Propriétés du serveur de publication** ;  
  
-   Exécute **sp_replicationdboption** et définit l’option **Publier** (pour les publications transactionnelles ou de capture instantanée) ou **publication de fusion** (pour les publications de fusion) à **True**.  
  
## Options  
 **Bases de données**  
 Permet de choisir le nom de la base de données contenant les données et les objets de base de données à publier.  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  