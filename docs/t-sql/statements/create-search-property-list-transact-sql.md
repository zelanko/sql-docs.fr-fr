---
title: "CRÉER la liste de propriétés de recherche (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SEARCH_PROPERTY_LIST_TSQL
- CREATE SEARCH
- CREATE_SEARCH_TSQL
- CREATE_SEARCH_PROPERTY_TSQL
- CREATE SEARCH PROPERTY
- CREATE SEARCH PROPERTY LIST
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], creating
- CREATE SEARCH PROPERTY LIST statement
ms.assetid: 5440cbb8-3403-4d27-a2f9-8e1f5a1bc12b
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b055be4f948b62553ddbabb40613971a0e5619d8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-search-property-list-transact-sql"></a>CREATE SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Crée une liste de propriétés de recherche. Une liste de propriétés de recherche permet de spécifier une ou plusieurs propriétés de recherche que vous souhaitez inclure dans un index de recherche en texte intégral.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE SEARCH PROPERTY LIST new_list_name  
   [ FROM [ database_name. ] source_list_name ]  
   [ AUTHORIZATION owner_name ]  
;  
```  
  
## <a name="arguments"></a>Arguments  
 *new_list_name*  
 Nom de la nouvelle liste des propriétés de recherche. *new_list_name* est un identificateur avec un maximum de 128 caractères. *new_list_name* doit être unique parmi toutes les listes de propriétés dans la base de données actuelle et sont conformes aux règles des identificateurs. *new_list_name* sera utilisé lors de la création de l’index de recherche en texte intégral.  
  
 *database_name*  
 Nom de la base de données dans laquelle la liste de propriétés spécifiée par *source_list_name* se trouve. Si non spécifié, *nom_base_de_données* par défaut, la base de données actuelle.  
  
 *database_name* doit spécifier le nom de la base de données existante. La connexion pour la connexion actuelle doit être associée à un ID utilisateur existant dans la base de données spécifiée par *nom_base_de_données*. Vous devez également avoir requis [autorisations](#Permissions) sur la base de données.  
  
 *source_list_name*  
 Spécifie que la nouvelle liste de propriétés est créée en copiant une liste de propriétés existante à partir de *nom_base_de_données*. Si *source_list_name* n’existe pas, CREATE SEARCH PROPERTY LIST les échoue avec une erreur. Les propriétés de recherche dans *source_list_name* sont héritées par *new_list_name*.  
  
 AUTORISATION *owner_name*  
 Spécifie le nom d'un utilisateur ou d'un rôle pour détenir la liste de propriétés. *owner_name* doit être le nom d’un rôle dont l’utilisateur actuel est membre ou l’utilisateur actuel doit avoir l’autorisation IMPERSONATE *owner_name*. En l'absence de spécification, la propriété revient à l'utilisateur actuel.  
  
> [!NOTE]  
>  Le propriétaire peut être modifié à l’aide de la [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]  
>  Pour plus d’informations sur la propriété de listes en général, consultez [recherche les propriétés de Document avec des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 Par défaut, une nouvelle liste des propriétés de recherche est vide et vous devez la modifier pour ajouter une ou plusieurs propriétés de recherche manuellement. Vous pouvez également copier une liste de propriétés de recherche existante. Dans ce cas, la nouvelle liste hérite des propriétés de recherche de sa source, mais vous pouvez modifier la nouvelle liste pour ajouter ou supprimer des propriétés de recherche. Toutes les propriétés figurant dans la liste des propriétés de recherche au moment du remplissage complet suivant sont incluses dans l'index de recherche en texte intégral.  
  
 Une instruction CREATE SEARCH PROPERTY LIST échoue si l'une des conditions suivantes se présente :  
  
-   Si la base de données spécifiée par *nom_base_de_données* n’existe pas.  
  
-   Si la liste spécifiée par *source_list_name* n’existe pas.  
  
-   Si vous ne possédez pas les autorisations appropriées.  
  
 **Pour ajouter ou supprimer des propriétés d’une liste**  
  
-   [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)  
  
-   **Pour supprimer une liste de propriétés**  
  
-   [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)  
  
##  <a name="Permissions"></a> Autorisations  
 Requiert des autorisations CREATE FULLTEXT CATALOG dans la base de données actuelle et des autorisations REFERENCES sur toute base de données depuis laquelle vous copiez une liste de propriétés source.  
  
> [!NOTE]  
>  L'autorisation REFERENCES est obligatoire pour associer la liste à un index de recherche en texte intégral. L'autorisation CONTROL est obligatoire pour ajouter et supprimer des propriétés ou supprimer la liste. Le propriétaire d'une liste de propriétés peut accorder des autorisations REFERENCES ou CONTROL sur la liste. Les utilisateurs disposant de l'autorisation CONTROL peuvent également accorder l'autorisation REFERENCES à d'autres utilisateurs.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-an-empty-property-list-and-associating-it-with-an-index"></a>A. Création d'une liste de propriétés vide et association à un index  
 L'exemple suivant crée une nouvelle liste de propriétés de recherche nommée `DocumentPropertyList`. L’exemple utilise ensuite un [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) instruction à associer la nouvelle liste de propriétés de l’index de recherche en texte intégral de la `Production.Document` de table dans le `AdventureWorks` base de données, sans démarrer un remplissage.  
  
> [!NOTE]  
>  Pour obtenir un exemple qui ajoute plusieurs propriétés de recherche prédéfinies et bien connues à cette liste de propriétés de recherche, consultez [ALTER SEARCH PROPERTY LIST &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-search-property-list-transact-sql.md). Après avoir ajouté des propriétés de recherche à la liste, l'administrateur de base de données devra utiliser une autre instruction ALTER FULLTEXT INDEX avec la clause START FULL POPULATION.  
  
```  
CREATE SEARCH PROPERTY LIST DocumentPropertyList;  
GO  
USE AdventureWorks2012;  
ALTER FULLTEXT INDEX ON Production.Document   
   SET SEARCH PROPERTY LIST DocumentPropertyList  
   WITH NO POPULATION;   
GO   
```  
  
### <a name="b-creating-a-property-list-from-an-existing-one"></a>B. Création d'une liste de propriétés à partir d'une liste existante  
 L'exemple suivant crée une nouvelle liste de propriétés de recherche, `JobCandidateProperties`, à partir de la liste créée par l'exemple A, `DocumentPropertyList`, associée à un index de recherche en texte intégral dans la base de données `AdventureWorks2012`. L'exemple utilise ensuite une instruction ALTER FULLTEXT INDEX pour associer la nouvelle liste de propriétés à l'index de recherche en texte intégral de la table `HumanResources.JobCandidate` dans la base de données `AdventureWorks2012`. Cette instruction ALTER FULLTEXT INDEX entraîne un remplissage complet, ce qui correspond au comportement par défaut de la clause SET SEARCH PROPERTY LIST.  
  
```  
CREATE SEARCH PROPERTY LIST JobCandidateProperties 
FROM AdventureWorks2012.DocumentPropertyList;  
GO  
ALTER FULLTEXT INDEX ON HumanResources.JobCandidate   
   SET SEARCH PROPERTY LIST JobCandidateProperties;  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/alter-search-property-list-transact-sql.md)   
 [DROP SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)   
 [Sys.registered_search_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [Sys.registered_search_property_lists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Sys.dm_fts_index_keywords_by_property &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [Rechercher des GUID du jeu de propriétés et des ID d’entier de propriétés pour les propriétés de recherche](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
  

