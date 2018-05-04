---
title: Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
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
- DMSCHEMA_MINING_SERVICE_PARAMETERS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_SERVICE_PARAMETERS rowset
ms.assetid: 5994e66b-84d0-4279-9f50-d92fd829dd83
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d64b63f6aae163e6703f7f2a7074f3c1e543adb6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="dmschemaminingserviceparameters-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_SERVICE_PARAMETERS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Ensembles de lignes de schéma de données d’exploration de données](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
