---
title: "Vues | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-views
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- views [SQL Server], about views
ms.assetid: ada83c28-e8b7-45d9-b53c-b3d67c8820c8
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ca3c02162484ebf4f12a8b98b1cad2b1aea89c22
ms.lasthandoff: 04/11/2017

---
# <a name="views"></a>Vues
  Une vue est une table virtuelle dont le contenu est défini par une requête. À l'instar d'une table, une vue est un ensemble de colonnes et de lignes nommées de données. À moins d'être indexée, elle n'existe pas en tant qu'ensemble de valeurs de données stocké dans une base de données. Les lignes et les colonnes de données proviennent de tables référencées dans la requête qui définit la vue et sont produites dynamiquement lorsque la vue est référencée.  
  
 Une vue fait office de filtre sur les tables sous-jacentes qui y sont référencées. La requête qui définit la vue peut émaner d'une ou de plusieurs tables ou d'autres vues de la base de données en cours ou d'autres bases de données. Les requêtes distribuées peuvent également être employées pour définir des vues qui utilisent des données provenant de plusieurs sources hétérogènes. Cela est particulièrement utile si vous souhaitez combiner des données de structure similaire issues de différents serveurs, chacun hébergeant des données relatives à une région différente de votre organisation.  
  
 Vous pouvez recourir aux vues pour affiner, simplifier et personnaliser la perception de la base de données par chaque utilisateur. Les vues peuvent être utilisées comme mécanismes de sécurité en permettant aux utilisateurs d'accéder aux données par le biais de la vue, sans leur accorder d'autorisations qui leur permettraient d'accéder directement aux tables de base sous-jacentes de la vue. Les vues peuvent servir à fournir une interface de compatibilité descendante afin d'émuler une table qui existait mais dont le schéma a changé. Cependant, vous pouvez aussi y recourir pour copier des données vers et à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d'améliorer les performances et de partitionner les données.  
  
## <a name="types-of-views"></a>Types de vues  
 Outre le rôle standard des vues de base définies par l'utilisateur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] met à votre disposition les types de vues suivants, qui remplissent une fonction particulière dans une base de données.  
  
 Vues indexées  
 Une vue indexée est une vue qui a été matérialisée, Cela signifie que la définition de la vue a été calculée et que les données résultantes sont stockées comme dans une table. Vous indexez une vue en créant un index cluster unique sur celle-ci. Les vues indexées peuvent améliorer considérablement les performances de certains types de requêtes. Les vues indexées sont les plus efficaces pour les requêtes qui agrègent de nombreuses lignes. Elles ne conviennent pas à des datasets sous-jacents qui sont fréquemment mis à jour.  
  
 Vues partitionnées  
 Une vue partitionnée joint horizontalement les données partitionnées d'un ensemble de tables membres sur un ou plusieurs serveurs. Les données sont ainsi affichées comme si elles provenaient d'une seule table. Une vue qui joint des tables membres sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est une vue partitionnée locale.  
  
 Vues système  
 Les vues système exposent les métadonnées de catalogue. Vous pouvez utiliser des vues système pour retourner des informations sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les objets définis dans l'instance. Par exemple, vous pouvez interroger la vue de catalogue sys.databases pour retourner des informations sur les bases de données définies par l’utilisateur disponibles dans l’instance. Pour plus d’informations, consultez [Vues système &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
## <a name="common-view-tasks"></a>Tâches courantes associées aux vues  
 Le tableau suivant fournit des liens vers les tâches couramment associées à la création ou à la modification d'une vue.  
  
|Tâches associées aux vues|Rubrique|  
|----------------|-----------|  
|Explique comment créer une vue.|[Créer des vues](../../relational-databases/views/create-views.md)|  
|Explique comment créer une vue indexée.|[Créer des vues indexées](../../relational-databases/views/create-indexed-views.md)|  
|Explique comment modifier la définition de la vue.|[Modifier des vues](../../relational-databases/views/modify-views.md)|  
|Explique comment modifier des données par le biais d'une vue.|[Modifier les données par l’intermédiaire d’une vue](../../relational-databases/views/modify-data-through-a-view.md)|  
|Explique comment supprimer une vue.|[Supprimer des vues](../../relational-databases/views/delete-views.md)|  
|Explique comment retourner des informations sur une vue comme la définition de la vue.|[Obtenir des informations au sujet d’une vue](../../relational-databases/views/get-information-about-a-view.md)|  
|Explique comment renommer une vue.|[Renommer des vues](../../relational-databases/views/rename-views.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des vues sur les colonnes XML](../../relational-databases/xml/create-views-over-xml-columns.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)  
  
  
