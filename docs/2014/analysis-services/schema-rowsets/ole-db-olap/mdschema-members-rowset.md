---
title: Ensemble de lignes MDSCHEMA_MEMBERS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_MEMBERS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEMBERS rowset
ms.assetid: 0b1aada0-67f8-4ef6-81b2-0100b65e0c2f
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d36a065ea73f249ce5c4d9dc37cc047ac864cb84
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280015"
---
# <a name="mdschemamembers-rowset"></a>Ensemble de lignes MDSCHEMA_MEMBERS
  Décrit les membres d'une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_MEMBERS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom de la base de données à laquelle ce membre appartient.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nom du schéma auquel ce membre appartient.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube auquel ce membre appartient.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique de la dimension à laquelle ce membre appartient.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique de la hiérarchie à laquelle ce membre appartient.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du niveau auquel ce membre appartient.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Distance du membre par rapport à la racine de la hiérarchie. Le niveau de la racine est égal à zéro (0).|  
|`MEMBER_ORDINAL`|`DBTYPE_UI4`||(Déconseillé) Renvoie toujours `0`.|  
|`MEMBER_NAME`|`DBTYPE_WSTR`||Nom du membre.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du membre.|  
|`MEMBER_TYPE`|`DBTYPE_I4`||Type du membre :<br /><br /> -   `MDMEMBER_TYPE_REGULAR` (`1`)<br />-   `MDMEMBER_TYPE_ALL` (`2`)<br />-   `MDMEMBER_TYPE_MEASURE` (`3`)<br />-   `MDMEMBER_TYPE_FORMULA` (`4`)<br />-   `MDMEMBER_TYPE_UNKNOWN` (`0`)<br />-   `MDMEMBER_TYPE_FORMULA` est prioritaire sur `MDMEMBER_TYPE_MEASURE`. Par exemple, si la dimension Measures comprend un membre de formule (calculé), ce dernier est répertorié sous la forme `MDMEMBER_TYPE_FORMULA`.|  
|`MEMBER_GUID`|`DBTYPE_GUID`||GUID du membre. `NULL` s'il n'existe aucun GUID.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`||Étiquette ou légende associée au membre. Principalement utilisée à des fins d'affichage. Si une légende n’existe pas, `MEMBER_NAME` est retournée.|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||Nombre d'enfants de ce membre. Ce nombre peut être une estimation ; il ne doit donc pas être considéré comme le nombre exact. Les fournisseurs doivent renvoyer la meilleure estimation possible.|  
|`PARENT_LEVEL`|`DBTYPE_UI4`||Distance du parent du membre par rapport au niveau racine de la hiérarchie. Le niveau de la racine est égal à zéro (0).|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||Nom unique du parent du membre. `NULL` est retournée pour tout membre situé au niveau de la racine.|  
|`PARENT_COUNT`|`DBTYPE_UI4`||Nombre de parents de ce membre.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Cette colonne retourne toujours une valeur `NULL`.<br /><br /> Cette colonne existe pour la compatibilité descendante|  
|`EXPRESSION`|`DBTYPE_WSTR`||Expression pour les calculs, si le membre est de type `MDMEMBER_TYPE_FORMULA`.|  
|`MEMBER_KEY`|`DBTYPE_WSTR`||Valeur de la colonne clé du membre. Retourne `NULL` si le membre possède une clé composite.|  
|`IS_PLACEHOLDERMEMBER`|`DBTYPE_BOOL`||Valeur booléenne qui indique si un membre est un membre d'espace réservé pour une position vide dans une hiérarchie de dimension.<br /><br /> Elle est valide uniquement si la propriété `MDX Compatibility` a été définie à 2.|  
|`IS_DATAMEMBER`|`DBTYPE_BOOL`||Valeur booléenne indiquant si le membre est un membre de données.<br /><br /> Retourne True si le membre est un membre de données.|  
|`SCOPE`|`DBTYPE_I4`||Étendue du membre. Le membre peut être un membre calculé de session ou un membre calculé global. La colonne retourne `NULL` pour les membres non calculés.<br /><br /> Les valeurs possibles pour cette colonne sont les suivantes :<br /><br /> -MDMEMBER_SCOPE_GLOBAL = 1<br />-MDMEMBER_SCOPE_SESSION = 2|  
|`Zero or more additional columns`|`DBTYPE_UI2`||Aucune propriété n'est retournée si les membres peuvent être retournés de plusieurs niveaux. Par exemple, si l'opérateur Tree est `PARENT` et `SELF` pour une hiérarchie de type enfant non parent, aucune propriété de membre n'est retournée.<br /><br /> Ceci s'applique aux hiérarchies déséquilibrées où les opérateurs d'arborescence peuvent retourner des membres de niveaux différents (par exemple, si le niveau précédent contient des trous et qu'un parent sur les membres est demandé).|  
  
 L'ensemble de lignes est trié selon `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME`, `LEVEL_UNIQUE_NAME`, `LEVEL_NUMBER`, `MEMBER_ORDINAL`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_MEMBERS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`|Facultatif.|  
|`MEMBER_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`|Facultatif.|  
|`MEMBER_TYPE`|`DBTYPE_I4`|Facultatif.|  
|`TREE_OP`|`DBTYPE_I4`|(Facultatif) S'applique uniquement à un membre unique :<br /><br /> -   `MDTREEOP_ANCESTORS` (`0x20`) retourne tous les ancêtres.<br />-   `MDTREEOP_CHILDREN` (`0x01`) retourne uniquement les enfants immédiats.<br />-   `MDTREEOP_SIBLINGS` (`0x02`) retourne les membres du même niveau.<br />-   `MDTREEOP_PARENT` (`0x04`) retourne uniquement le parent immédiat.<br />-   `MDTREEOP_SELF` (`0x08`) retourne lui-même dans la liste des lignes retournées.<br />-   `MDTREEOP_DESCENDANTS` (`0x10`) retourne tous les descendants.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -CUBE 1<br />-DIMENSION DE 2<br /><br /> La restriction par défaut est la valeur 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
