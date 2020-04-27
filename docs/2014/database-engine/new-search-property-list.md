---
title: Nouvelle liste de propriétés de recherche | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2aff15a42c8bffeb5a54e92b9ce7a09ace282ce4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774498"
---
# <a name="new-search-property-list"></a>Nouvelle liste de propriétés de recherche
  Utilisez cette boîte de dialogue pour créer une liste de propriétés de recherche.  
  
## <a name="options"></a>Options  
 **Nom de la liste de propriétés de recherche**  
 Entrez le nom de la liste de propriétés de recherche.  
  
 **Propriétaire**  
 Spécifiez le propriétaire de la liste de propriétés de recherche. Si vous souhaitez que la propriété vous soit assignée à vous, à savoir, l'utilisateur actuel, laissez ce champ vide. Cliquez sur le bouton Parcourir pour spécifier un autre utilisateur.  
  
### <a name="create-search-property-list-options"></a>Options de création de listes de propriétés de recherche  
 Cliquez sur l'une des options suivantes :  
  
 **Créer une liste de propriétés de recherche vide**  
 Crée une liste de propriétés de recherche sans propriété.  
  
 **Créer à partir d'une liste de propriétés de recherche existante**  
 Copie les propriétés d'une liste de propriétés de recherche existante dans la nouvelle liste de propriétés. Les listes de propriétés de recherche sont des objets de base de données. Vous devez donc spécifier la base de données qui contient la liste de propriétés que vous souhaitez copier.  
  
 **Base de données source**  
 Spécifiez le nom de la base de données à laquelle appartient la liste de propriétés de recherche existante. La base de données actuelle est sélectionnée par défaut. Vous pouvez éventuellement utiliser la zone de liste pour sélectionner une autre base de données, si votre connexion actuelle est associée à un ID d'utilisateur dans cette base de données.  
  
 **Liste de propriétés de recherche source**  
 Sélectionnez le nom d'une liste de propriétés de recherche existante parmi celles appartenant à la base de données sélectionnée.  
  
## <a name="permissions"></a>Autorisations  
 Consultez [créer une liste de propriétés de recherche &#40;&#41;Transact-SQL ](/sql/t-sql/statements/create-search-property-list-transact-sql).  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>Pour utiliser SQL Server Management Studio pour gérer des listes de propriétés de recherche  
 Pour plus d'informations sur la façon de créer, afficher, modifier ou supprimer une liste de propriétés de recherche et sur la configuration d'un index de recherche en texte intégral pour la recherche de propriétés, consultez [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une liste de propriétés de recherche &#40;&#41;Transact-SQL](/sql/t-sql/statements/create-search-property-list-transact-sql)   
 [Rechercher des propriétés de document avec des listes de propriétés de recherche](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
