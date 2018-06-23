---
title: Mapper des relations plusieurs-à-plusieurs (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4dd38759ccd32621f31da1c0e078a4cf5c344c2d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153854"
---
# <a name="map-many-to-many-relationships-visual-database-tools"></a>Mapper des relations plusieurs-à-plusieurs (Visual Database Tools)
  Les relations plusieurs-à-plusieurs vous permettent de mettre chaque ligne d'une table en relation avec plusieurs lignes d'une autre table, et vice versa. Par exemple, vous pouvez créer une relation plusieurs-à-plusieurs entre la table `authors` et la table `titles` pour établir une correspondance entre chaque auteur et tous ses livres, entre chaque livre et tous ses auteurs. Si vous choisissiez de créer une relation un-à-plusieurs à partir de l'une ou l'autre table, chaque livre ne pourrait renvoyer qu'à un seul auteur ou chaque auteur qu'à un seul livre.  
  
 Les relations plusieurs-à-plusieurs entre les tables sont enregistrées dans les bases de données au moyen de tables de jonctions. Une table de jonction contient les colonnes clés primaire des deux tables à mettre en relation. Vous créez ensuite une relation entre les colonnes clés primaire de chacune des deux tables et les colonnes correspondantes dans la table de jonction. Dans la base de données pubs, la table `titleauthor` est une table de jonction.  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a>Pour créer une relation plusieurs-à-plusieurs entre des tables  
  
1.  Dans votre schéma de base de données, ajoutez les tables entre lesquelles vous voulez créer une relation plusieurs-à-plusieurs.  
  
2.  Créez une troisième table : cliquez avec le bouton droit sur le schéma, puis, dans le menu contextuel, cliquez sur **Nouvelle table** . Cette table sera la table de jonction.  
  
3.  Dans la boîte de dialogue **Choisir un nom** , changez le nom de la table assigné par le système. Par exemple, la table de jonction entre les tables `titles` et `authors` s'intitule à présent `titleauthors`.  
  
4.  Copiez les colonnes clés primaire de chacune des deux autres tables vers la table de jonction. Vous pouvez ajouter d'autres colonnes à cette table comme à n'importe quelle autre table.  
  
5.  Dans la table de jonction, configurez la clé primaire de façon à inclure toutes les colonnes clés primaire des deux autres tables. Pour plus d’informations, consultez [créer des clés primaires](../../relational-databases/tables/create-primary-keys.md).  
  
6.  Définissez une relation un-à-plusieurs entre chacune des deux tables primaires et la table de jonction. La table de jonction doit se trouver du côté « plusieurs » des deux relations créées. Pour plus d’informations, consultez [créer des relations de clé étrangère](../../relational-databases/tables/create-foreign-key-relationships.md).  
  
    > [!NOTE]  
    >  Lorsque vous créez une table de jonction dans un schéma de base de données, les données des tables connexes ne sont pas insérées dans la table de jonction. Pour plus d’informations sur l’insertion de données dans une table, consultez [Créer des requêtes Insert Results &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des schémas de base de données &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md)  
  
  