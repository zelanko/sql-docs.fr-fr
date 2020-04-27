---
title: Base de données de publication | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.publicationdatabase.f1
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cb31bae59d95b01279a9fa84e02cd22c8017ca14
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63021748"
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
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)   
 [Create a Publication](publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)  
  
  
