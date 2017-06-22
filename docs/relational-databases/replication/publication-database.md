---
title: "Base de données de publication | Microsoft Docs"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3f29e1319d78cb2fadca134b78abdfc748e11c67
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="publication-database"></a>Base de données de publication
  La base de données de publication est la base de données située sur le serveur de publication, qui sert de source aux données et aux objets de base de données à répliquer. Chaque base de données de publication mise en œuvre lors de la réplication doit obligatoirement être activée. La base de données est activée lorsqu'un membre du rôle serveur fixe **sysadmin** :  
  
-   crée une publication relative à la base de données par le biais de l'Assistant Nouvelle publication ;  
  
-   sélectionne la base de données dans la boîte de dialogue **Propriétés du serveur de publication** ;  
  
-   exécute **sp_replicationdboption** et attribue à l'option **publish** (dans le cas de publications d'instantanés ou de publications transactionnelles) ou à l'option **merge publish** (dans le cas de publications de fusion) la valeur **True**.  
  
## <a name="options"></a>Options  
 **Bases de données**  
 Permet de choisir le nom de la base de données contenant les données et les objets de base de données à publier.  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Créer une publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  
