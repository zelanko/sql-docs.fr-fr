---
title: Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_SERVICE_PARAMETERS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c84d263a312318be40c65c37a168bf11fdc97cfc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS
  Décrit les paramètres des algorithmes sur le serveur.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DMSCHEMA_MINING_SERVICE_PARAMETERS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type| Description|  
|-----------------|--------------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Nom de l'algorithme.|  
|**NOM_PARAMÈTRE**|**DBTYPE_WSTR**|Nom du paramètre.|  
|**TYPE_PARAMÈTRE**|**DBTYPE_WSTR**|Type du paramètre.|  
|**IS_REQUIRED**|**DBTYPE_BOOL**|Valeur booléenne qui retourne **TRUE** si le paramètre est requis.|  
|**PARAMETER_FLAGS**|**DBTYPE_UI4**|Masque de bits qui décrit les caractéristiques du paramètre :<br /><br /> **DM_PARAMETER_TRAINING** (**0x0000001**) indique que le paramètre est utilisé pour l'apprentissage<br /><br /> **DM_PARAMETER_PREDICTION** (**0x00000002**) indique que le paramètre est utilisé pour la prédiction<br /><br /> **DM_PARAMETER_CONTENT** (**0x00000003**) indique que le paramètre est utilisé pour la restriction de contenu|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Description conviviale du paramètre.|  
|**VALEUR PAR DÉFAUT**|**DBTYPE_WSTR**|Valeur par défaut du paramètre. Retourne **NULL** si la valeur par défaut n'est pas un type de données simple.|  
|**VALUE_ENUMERATION**|**DBTYPE_WSTR**|Énumérateur des valeurs possibles du paramètre.|  
|**HELP_FILE**|**DBTYPE_WSTR**|Nom du fichier qui contient la documentation de ce paramètre.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|ID de contexte d'aide de cette fonction.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DMSCHEMA_MINING_SERVICE_PARAMETERS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**NOM_PARAMÈTRE**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
