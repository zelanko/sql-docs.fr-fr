---
title: Ensemble de lignes DMSCHEMA_MINING_STRUCTURES | Documents Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DMSCHEMA_MINING_STRUCTURES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c7d06d5e417b97b42791acb3dc16c939a347e2ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="dmschemaminingstructures-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_STRUCTURES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fournit des informations sur les structures d'exploration de données contenues dans le catalogue actuel.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DMSCHEMA_MINING_STRUCTURES** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||Nom du catalogue.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||Nom de schéma non qualifié. **NULL** si les schémas ne sont pas pris en charge par le fournisseur.|  
|**NOM_STRUCTURE**|**DBTYPE_WSTR**||Nom de la structure. Cette colonne ne peut pas contenir de valeur **NULL**.|  
|**STRUCTURE_GUID**|**DBTYPE_GUID**||GUID qui identifie la structure de manière unique. **NULL** si les ID de propriété ne sont pas pris en charge par le fournisseur.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Description concise de la structure. **NULL** si aucune description n'est associée à la structure.|  
|**STRUCTURE_PROPID**|**DBTYPE_UI4**||ID de propriété de la structure. **NULL** si les ID de propriété ne sont pas pris en charge par le fournisseur.|  
|**DATE_DE_CRÉATION**|**DBTYPE_DBTIMESTAMP**||Date de création de la structure. **NULL** si cette valeur n'est pas disponible auprès du fournisseur.|  
|**DATE_DE_MODIFICATION**|**DBTYPE_DBTIMESTAMP**||Date de dernière modification de la structure. **NULL** si cette valeur n'est pas disponible auprès du fournisseur.|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**||(Facultatif) Instruction utilisée pour créer le modèle d'exploration de données d'origine.|  
|**IS_POPULATED**|**DBTYPE_BOOL**||Valeur booléenne qui indique si la structure est remplie.<br /><br /> **VARIANT_TRUE** si la structure est remplie ; **VARIANT_FALSE** dans le cas contraire.|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**||Date du dernier traitement de la structure. **NULL** si cette valeur n'est pas disponible auprès du fournisseur.|  
|**HOLDOUT_MAXPERCENT**|**DBTYPE_ UI1**||Valeur spécifiée par l'utilisateur qui indique le pourcentage maximal de cas d'entrée exclus en tant que jeu de test.<br /><br /> 0 ou **NULL** indique qu'il n'existe aucune limite.|  
|**HOLDOUT_MAXCASES**|**DBTYPE_UI8**||Valeur spécifiée par l'utilisateur qui indique le nombre maximal de cas d'entrée exclus en tant que jeu de test.<br /><br /> 0 ou **NULL** indique qu'il n'existe aucune limite.|  
|**HOLDOUT_SEED**|**DBTYPE_UI8**||Valeur spécifiée par l'utilisateur qui est employée comme valeur de départ pour le partitionnement répété.<br /><br /> La valeur 0 indique qu'un hachage de l'ID de la structure d'exploration de données est employé comme valeur de départ.|  
|**HOLDOUT_ACTUAL_SIZE**|**DBTYPE_UI8**||Si la structure d'exploration de données est traitée, cette valeur indique la taille réelle du jeu de données de test, exprimée en nombre de cas.<br /><br /> **NULL** indique que la structure d'exploration de données n'est pas traitée.|  
  
 L'ensemble de lignes est trié selon **STRUCTURE_CATALOG**, **STRUCTURE_SCHEMA**, **STRUCTURE_NAME**.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DMSCHEMA_MINING_STRUCTURES** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**NOM_STRUCTURE**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma de données d’exploration de données](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
