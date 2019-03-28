---
title: sp_help_spatial_geography_histogram (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_histogram_TSQL
- sp_help_spatial_geography_histogram
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_histogram
ms.assetid: 5c5bd319-055d-4cd6-8c5a-06354cc056cc
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a6fa55cd5359c64f2a124ff85429745c995fae96
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538161"
---
# <a name="sphelpspatialgeographyhistogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Facilite le codage des paramètres de grille pour un index spatial.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_spatial_geography_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @sample = ] 'tablesample' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @tabname = ] 'tabname'` Est le nom qualifié ou non de la table pour laquelle l’index spatial a été spécifié.  
  
 Les guillemets ne sont nécessaires que si une une table qualifiée est spécifiée. Si un nom qualifié complet (incluant un nom de base de données) est fourni, le nom de base de données doit être celui de la base de données active. *tabname* est **sysname**, sans valeur par défaut.  
  
`[ @colname = ] 'columnname'` Est le nom de la colonne spatiale spécifiée. *ColumnName* est un **sysname**, sans valeur par défaut.  
  
`[ @resolution = ] 'resolution'` Est la résolution du rectangle englobant. Les valeurs possibles sont comprises entre 10 et 5000. *résolution* est un **tinyint**, sans valeur par défaut.  
  
`[ @sample = ] 'sample'` Est le pourcentage de la table qui est utilisé. Les valeurs valides sont compris entre 0 et 100. *TABLESAMPLE* est un **float**. Valeur par défaut est 100.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Une valeur de table est retournée. La grille suivante décrit le contenu de colonne de la table.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**cellid**|**Int**|Représente l'ID unique de chaque cellule, avec un nombre initial de 1.|  
|**cell**|**geography**|Polygone rectangulaire qui représente chaque cellule. La forme de cellule est identique à la forme de cellule utilisée pour l'indexation spatiale.|  
|**row_count**|**bigint**|Indique le nombre d'objets spatiaux qui touchent ou contiennent la cellule.|  
  
## <a name="permissions"></a>Autorisations  
 Utilisateur doit être un membre de la **public** rôle. Nécessite une autorisation READ ACCESS sur le serveur et l'objet.  
  
## <a name="remarks"></a>Notes  
 L'onglet spatial SSMS affiche une représentation graphique des résultats. Vous pouvez interroger les résultats dans la fenêtre spatiale afin d'obtenir un nombre approximatif d'éléments de résultat.  
  
> [!NOTE]  
>  Les objets dans la table peuvent couvrir plusieurs cellules ; par conséquent, la somme de cellules de la table peut être supérieure au nombre d'objets réels.  
  
 Cadre englobant pour le **geography** type est le globe entier.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant appelle **sp_help_spatial_geography_histogram** sur le `Person.Address` table dans le [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] base de données.  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées d’Index spatial &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
