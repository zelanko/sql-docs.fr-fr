---
title: Ensemble de lignes DMSCHEMA_MINING_STRUCTURES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_STRUCTURES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab600b39e4a8347e470153cf21510554605d1c71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323069"
---
# <a name="dmschemaminingstructures-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_STRUCTURES
  Fournit des informations sur les structures d'exploration de données contenues dans le catalogue actuel.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DMSCHEMA_MINING_STRUCTURES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||Nom du catalogue.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||Nom de schéma non qualifié. `NULL` si les schémas ne sont pas pris en charge par le fournisseur.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||Nom de la structure. Cette colonne ne peut pas contenir `NULL`.|  
|`STRUCTURE_GUID`|`DBTYPE_GUID`||GUID qui identifie la structure de manière unique. `NULL` si les ID de propriété ne sont pas pris en charge par le fournisseur.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description concise de la structure. `NULL` si aucune description n'est associée à la structure.|  
|`STRUCTURE_PROPID`|`DBTYPE_UI4`||ID de propriété de la structure. `NULL` si les ID de propriété ne sont pas pris en charge par le fournisseur.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Date de création de la structure. `NULL` si cette valeur n'est pas disponible auprès du fournisseur.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Date de dernière modification de la structure. `NULL` si cette valeur n'est pas disponible auprès du fournisseur.|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||(Facultatif) Instruction utilisée pour créer le modèle d'exploration de données d'origine.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Valeur booléenne qui indique si la structure est remplie.<br /><br /> `VARIANT_TRUE` si la structure est remplie ; `VARIANT_FALSE` dans le cas contraire.|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||Date du dernier traitement de la structure. `NULL` si cette valeur n'est pas disponible auprès du fournisseur.|  
|`HOLDOUT_MAXPERCENT`|`DBTYPE_ UI1`||Valeur spécifiée par l'utilisateur qui indique le pourcentage maximal de cas d'entrée exclus en tant que jeu de test.<br /><br /> 0 ou `NULL` indique qu'il n'existe aucune limite.|  
|`HOLDOUT_MAXCASES`|`DBTYPE_UI8`||Valeur spécifiée par l'utilisateur qui indique le nombre maximal de cas d'entrée exclus en tant que jeu de test.<br /><br /> 0 ou `NULL` indique qu'il n'existe aucune limite.|  
|`HOLDOUT_SEED`|`DBTYPE_UI8`||Valeur spécifiée par l'utilisateur qui est employée comme valeur de départ pour le partitionnement répété.<br /><br /> La valeur 0 indique qu'un hachage de l'ID de la structure d'exploration de données est employé comme valeur de départ.|  
|`HOLDOUT_ACTUAL_SIZE`|`DBTYPE_UI8`||Si la structure d'exploration de données est traitée, cette valeur indique la taille réelle du jeu de données de test, exprimée en nombre de cas.<br /><br /> `NULL` indique que la structure d'exploration de données n'est pas traitée.|  
  
 L'ensemble de lignes est trié selon `STRUCTURE_CATALOG`, `STRUCTURE_SCHEMA`, `STRUCTURE_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DMSCHEMA_MINING_STRUCTURES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|Facultatif.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|Facultatif.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
