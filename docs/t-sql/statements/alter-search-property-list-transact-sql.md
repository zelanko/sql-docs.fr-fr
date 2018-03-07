---
title: ALTER SEARCH PROPERTY LIST (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SEARCH_PROPERTY_TSQL
- ALTER_SEARCH_PROPERTY_LIST_TSQL
- ALTER SEARCH PROPERTY LIST
- ALTER SEARCH PROPERTY
- ALTER_SEARCH_TSQL
- ALTER SEARCH
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], search property lists
- search property lists [SQL Server], altering
- ALTER SEARCH PROPERTY LIST statement
ms.assetid: 0436e4a8-ca26-4d23-93f1-e31e2a1c8bfb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b56d1ae0be7a8aaef93011d6ecfde378a3e8fe91
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="alter-search-property-list-transact-sql"></a>ALTER SEARCH PROPERTY LIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ajoute une propriété de recherche spécifiée à la liste de propriétés de recherche spécifiée ou la supprime de cette liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ALTER SEARCH PROPERTY LIST list_name  
{  
   ADD 'property_name'  
     WITH   
      (   
          PROPERTY_SET_GUID = 'property_set_guid'  
        , PROPERTY_INT_ID = property_int_id  
      [ , PROPERTY_DESCRIPTION = 'property_description' ]  
      )  
 | DROP 'property_name'   
}  
;  
```  
  
## <a name="arguments"></a>Arguments  
 *Nom_liste*  
 Nom de la liste de propriétés modifiée. *Nom_liste* est un identificateur.  
  
 Pour afficher les noms des listes de propriétés existantes, utilisez le [sys.registered_search_property_lists](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md) affichage catalogue comme suit :  
  
```  
SELECT name FROM sys.registered_search_property_lists;  
```  
  
 ADD  
 Ajoute une propriété de recherche spécifié à la liste de propriétés spécifiée par *Nom_liste*. Cette propriété est enregistrée pour la liste de propriétés de recherche. Avant que les propriétés récemment ajoutées puissent être utilisées pour la recherche de propriétés, l'index ou les index de recherche en texte intégral associé doivent être remplis à nouveau. Pour plus d’informations, consultez [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md).  
  
> [!NOTE]  
>  Pour ajouter une propriété de recherche donnée à une liste de propriétés de recherche, vous devez fournir son GUID du jeu de propriétés (*clauses property_set_guid*) et l’ID entier de propriété (*paramètre property_int_id*). Pour plus d'informations, consultez la section« Obtention de GUID de jeux de propriétés et d'identificateurs », dans la suite de cette rubrique.  
  
 *property_name*  
 Spécifie le nom à utiliser pour identifier la propriété dans les requêtes de texte intégral. *property_name* doit identifier de façon unique la propriété dans le jeu de propriétés. Un nom de propriété peut contenir des espaces internes. La longueur maximale de *property_name* est de 256 caractères. Ce nom peut être un nom convivial, telles que l’auteur ou une adresse personnelle, ou il peut être le nom canonique Windows de la propriété, tel que **System.Author** ou **System.Contact.HomeAddress**.  
  
 Les développeurs souhaiteront utiliser la valeur que vous spécifiez pour *property_name* pour identifier la propriété dans le [CONTAINS](../../t-sql/queries/contains-transact-sql.md) prédicat. Par conséquent, lorsque Ajout d’une propriété, il est important de spécifier une valeur qui représente la propriété définie par la propriété spécifiée de manière significative la valeur GUID (*clauses property_set_guid*) et l’identificateur de la propriété (*paramètre property_int_id*). Pour plus d'informations sur les noms de propriété, consultez la section « Notes », plus loin dans cette rubrique.  
  
 Pour afficher les noms des propriétés qui existent actuellement dans une liste de propriétés de recherche de la base de données actuelle, utilisez la [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) affichage catalogue comme suit :  
  
```  
SELECT property_name FROM sys.registered_search_properties;  
```  
  
 Clauses PROPERTY_SET_GUID ='*clauses property_set_guid*'  
 Spécifie l'identificateur du jeu de propriétés auquel appartient la propriété. Il s'agit d'un identificateur global unique (GUID). Pour plus d'informations sur l'obtention de cette valeur, consultez les « Notes », dans la suite de cette rubrique.  
  
 Pour afficher la propriété GUID du jeu d’une propriété qui existe dans une liste de propriétés de recherche de la base de données actuelle, utilisez la [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) affichage catalogue comme suit :  
  
```  
SELECT property_set_guid FROM sys.registered_search_properties;  
```  
  
 Paramètre PROPERTY_INT_ID =*paramètre property_int_id*  
 Spécifie l'entier qui identifie la propriété dans son jeu de propriétés. Pour plus d'informations sur l'obtention de cette valeur, consultez la section « Notes ».  
  
 Pour afficher l’identificateur entier d’une propriété qui existe dans une liste de propriétés de recherche de la base de données actuelle, utilisez la [sys.registered_search_properties](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md) affichage catalogue comme suit :  
  
```  
SELECT property_int_id FROM sys.registered_search_properties;  
```  
  
> [!NOTE]  
>  Une combinaison donnée de *clauses property_set_guid* et *paramètre property_int_id* doit être unique dans une liste de propriétés de recherche. Si vous essayez d'ajouter une combinaison existante, l'opération ALTER SEARCH PROPERTY LIST échoue et génère une erreur. Cela signifie que vous pouvez définir uniquement un nom pour une propriété donnée.  
  
 PROPERTY_DESCRIPTION ='*property_description*'  
 Spécifie une description définie par l'utilisateur de la propriété. *PROPERTY_DESCRIPTION* est une chaîne de jusqu'à 512 caractères. Cette option est facultative.  
  
 DROP  
 Supprime la propriété spécifiée à partir de la liste de propriétés spécifiée par *Nom_liste*. La suppression d'une propriété annule son inscription ; elle ne peut donc plus faire l'objet d'une recherche.  
  
## <a name="remarks"></a>Notes  
 Chaque index de recherche en texte intégral ne peut avoir qu'une seule liste de propriétés de recherche.  
  
 Pour permettre l'interrogation sur une propriété de recherche donnée, vous devez l'ajouter à la liste des propriétés de recherche de l'index de recherche en texte intégral, puis remplir à nouveau l'index.  
  
 Lors de la spécification d'une propriété, vous pouvez réorganiser les clauses PROPERTY_SET_GUID, PROPERTY_INT_ID et PROPERTY_DESCRIPTION dans n'importe quel ordre, comme une liste séparée par des virgules mise entre parenthèses. Exemple :  
  
```  
ALTER SEARCH PROPERTY LIST CVitaProperties  
ADD 'System.Author'   
WITH (   
      PROPERTY_DESCRIPTION = 'Author or authors of a given document.',  
      PROPERTY_SET_GUID   = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9',   
      PROPERTY_INT_ID = 4   
      );  
```  
  
> [!NOTE]  
>  Cet exemple utilise le nom de la propriété, `System.Author`, qui est semblable au concept de noms de propriété canoniques présenté dans Windows Vista (nom canonique Windows).  
  
## <a name="obtaining-property-values"></a>Obtention de valeurs de propriété  
 La recherche en texte intégral mappe une propriété de recherche à un index de recherche en texte intégral à l'aide de son GUID du jeu de propriétés et d'un identificateur de propriété entier. Pour plus d’informations sur la façon d’obtenir ces valeurs pour les propriétés qui ont été définies par Microsoft, consultez [GUID du jeu de propriété trouver et Property Integer IDs for Search Properties](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md). Pour plus d'informations sur les propriétés définies par un éditeur de logiciels indépendant (ISV), consultez la documentation de ce dernier.  
  
## <a name="making-added-properties-searchable"></a>Recherche possible avec des propriétés ajoutées  
 L'ajout d'une propriété de recherche à une liste de propriétés de recherche permet d'inscrire la propriété. Une propriété ajoutée récemment peut être spécifiée immédiatement dans [CONTAINS](../../t-sql/queries/contains-transact-sql.md) requêtes. Toutefois, les requêtes de texte intégral avec étendue aux propriétés sur une propriété ajoutée récemment ne retourneront pas de documents tant que l'index de recherche en texte intégral associé n'aura pas été à nouveau rempli. Par exemple, la portée de propriété requête suivante sur une propriété ajoutée récemment, *new_search_property*, ne retournera pas de documents tant que l’index de recherche en texte intégral associé à la table cible (*table_name*) est rempli à nouveau :  
  
```  
SELECT column_name  
FROM table_name  
WHERE CONTAINS( PROPERTY( column_name, 'new_search_property' ), 
               'contains_search_condition');  
GO   
```  
  
 Pour démarrer un remplissage complet, utilisez ce qui suit [ALTER FULLTEXT INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-fulltext-index-transact-sql.md) instruction :  
  
```  
USE database_name;  
GO  
ALTER FULLTEXT INDEX ON table_name START FULL POPULATION;  
GO  
```  
  
> [!NOTE]  
>  Le remplissage n'est pas nécessaire après la suppression d'une propriété d'une liste de propriétés, car seules les propriétés qui restent dans la liste des propriétés de recherche sont disponibles pour l'interrogation en texte intégral.  
  
## <a name="related-references"></a>Références connexes  
 **Pour créer une liste de propriétés**  
  
-   [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)  
  
 **Pour supprimer une liste de propriétés**  
  
-   [DROP SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)  
  
 **Pour ajouter ou supprimer une liste de propriétés sur un index de recherche en texte intégral**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
 **Pour exécuter un remplissage sur un index de recherche en texte intégral**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-index-transact-sql.md)  
  
##  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation CONTROL sur la liste de propriétés.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-adding-a-property"></a>A. Ajout d'une propriété  
 L'exemple suivant ajoute plusieurs propriétés (`Title`, `Author` et `Tags`) à une liste de propriétés nommée `DocumentPropertyList`.  
  
> [!NOTE]  
>  Pour obtenir un exemple qui crée `DocumentPropertyList` liste de propriétés, consultez [CREATE SEARCH PROPERTY LIST &#40; Transact-SQL &#41; ](../../t-sql/statements/create-search-property-list-transact-sql.md).  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
   ADD 'Title'   
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 2,   
      PROPERTY_DESCRIPTION = 'System.Title - Title of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Author'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 4,   
      PROPERTY_DESCRIPTION = 'System.Author - Author or authors of the item.' );  
  
ALTER SEARCH PROPERTY LIST DocumentPropertyList   
    ADD 'Tags'  
   WITH ( PROPERTY_SET_GUID = 'F29F85E0-4FF9-1068-AB91-08002B27B3D9', PROPERTY_INT_ID = 5,   
      PROPERTY_DESCRIPTION = 
          'System.Keywords - Set of keywords (also known as tags) assigned to the item.' );  
```  
  
> [!NOTE]  
>  Vous devez associer une liste de propriétés de recherche donnée à un index de recherche en texte intégral avant de pouvoir l'utiliser dans le cadre de requêtes avec étendue aux propriétés. Pour ce faire, utilisez un [ALTER FULLTEXT INDEX](../../t-sql/statements/alter-fulltext-index-transact-sql.md) instruction et spécifiez la clause SET SEARCH PROPERTY LIST.  
  
### <a name="b-dropping-a-property"></a>B. Suppression d'une propriété  
 L'exemple suivant supprime la propriété `Comments` dans la liste de propriétés `DocumentPropertyList`.  
  
```  
ALTER SEARCH PROPERTY LIST DocumentPropertyList  
DROP 'Comments' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une liste de propriétés de recherche &#40; Transact-SQL &#41;](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [DROP SEARCH PROPERTY LIST &#40; Transact-SQL &#41;](../../t-sql/statements/drop-search-property-list-transact-sql.md)   
 [Sys.registered_search_properties &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)   
 [Sys.registered_search_property_lists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [Sys.dm_fts_index_keywords_by_property &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-property-transact-sql.md)   
 [Rechercher les propriétés du document à l’aide des listes de propriétés de recherche](../../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [Rechercher des GUID du jeu de propriétés et des ID d’entier de propriétés pour les propriétés de recherche](../../relational-databases/search/find-property-set-guids-and-property-integer-ids-for-search-properties.md)  
  
  
