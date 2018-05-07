---
title: Ensemble de lignes DMSCHEMA_MINING_FUNCTIONS | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f92a3028f9397283f8d5820c54d823e40b8fdc3d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="dmschemaminingfunctions-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_FUNCTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Décrit les fonctions d'exploration de données prises en charge par les algorithmes d'exploration de données disponibles sur un serveur exécutant [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DMSCHEMA_MINING_FUNCTIONS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**||Nom de l'algorithme.|  
|**NOM DE LA FONCTION**|**DBTYPE_WSTR**||Nom de la fonction.|  
|**FUNCTION_SIGNATURE**|**DBTYPE_WSTR**||Signature de la fonction.|  
|**RETURNS_TABLE**|**DBTYPE_BOOL**||**FALSE** si la fonction retourne le contenu scalaire (tel que la longueur de l'argument de caractère) ; **TRUE** si la fonction retourne une table (telle qu'une table d'histogrammes).|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Description conviviale de la fonction.|  
|**HELP_FILE**|**DBTYPE_WSTR**||Nom du fichier qui contient la documentation de cette fonction.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||ID de contexte d'aide de cette fonction.|  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DMSCHEMA_MINING_FUNCTIONS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**SERVICE_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**NOM DE LA FONCTION**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma de données d’exploration de données](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
