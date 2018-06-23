---
title: Nouvelle recherche en texte intégral liste de mots vides (Page Général) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5217bd995855ff33e6b21b883c854cb3db474e03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052914"
---
# <a name="new-full-text-stoplist-general-page"></a>Nouvelle liste de mots vides de texte intégral (page Général)
  Utilisez cette boîte de dialogue pour créer une liste de mots vides de texte intégral. Une *liste de mots vides* est un ensemble de mots couramment utilisés, appelés *mots vides*, qui sont omis de l'indexation de texte intégral pour les tables qui utilisent cette liste. Pour plus d’informations, consultez [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../relational-databases/search/full-text-search.md).  
  
 **Pour utiliser SQL Server Management Studio pour créer une liste de mots vides**  
  
-   [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Options  
 **Nom de la liste de mots vides en texte intégral**  
 Entrez le nom de la liste de mots vides de texte intégral.  
  
 **Propriétaire**  
 Spécifiez le propriétaire de la liste de mots vides de texte intégral. Si vous souhaitez que la propriété vous soit assignée à vous, à savoir, l'utilisateur actuel, laissez ce champ vide.  
  
 Cliquez sur le bouton Parcourir pour spécifier un autre utilisateur.  
  
### <a name="create-stoplist-options"></a>Options de création de liste de mots vides  
 Cliquez sur l'une des options de création suivantes :  
  
 **Créer une liste de mots vides vide**  
 La nouvelle liste de mots vides ne contiendra pas de mots vides.  
  
 **Créer à partir de la liste de mots vides système**  
 La nouvelle liste de mots vides est créée à partir de la liste de mots vides qui existe par défaut dans la [base de données Resource](../relational-databases/databases/resource-database.md).  
  
 **Créer à partir d'une liste de mots vides de texte intégral existante**  
 La nouvelle liste de mots vides est créée en copiant une liste de mots vides existante.  
  
 **base de données source**  
 Spécifie le nom de la base de données à laquelle appartient la liste de mots vides existante. La base de données actuelle est sélectionnée par défaut. Vous pouvez si vous le souhaitez sélectionner une autre base de données dans la zone de liste.  
  
 **Liste de mots vides source**  
 Spécifie le nom d'une liste de mots vides existante. Dans la liste des listes de mots vides disponibles, sélectionnez celle qui doit être utilisée comme source. Les listes de mots vides disponibles sont répertoriées dans l'ordre dans lequel elles apparaissent dans l'Explorateur d'objets.  
  
 Si des langues spécifiées dans les mots vides de la liste de mots vides source ne sont pas inscrits dans la base de données actuelle, l'exécution de CREATE FULLTEXT STOPLIST réussit, mais des avertissements sont retournés et les mots vides correspondants ne sont pas ajoutés.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)   
 [Configurer et gérer les mots vides et listes de mots vides pour la recherche en texte intégral](../relational-databases/search/full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
