---
title: Ensemble de lignes DMSCHEMA_MINING_MODEL_XML | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DMSCHEMA_MINING_MODEL_XML
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ad9e631d4f434fbab098fe1d93df86c009104f38
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="dmschemaminingmodelxml-rowset"></a>Ensemble de lignes DMSCHEMA_MINING_MODEL_XML
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Retourne la structure XML du modèle d’exploration de données. Le format de la chaîne XML est conforme au standard PMML (Predictive Model Markup Language) 2.1.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DMSCHEMA_MINING_MODEL_XML** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Nom du catalogue. Défini d'après le nom de la base de données dont le modèle est membre.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Nom de schéma non qualifié. Cette colonne n’est pas pris en charge par [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; il contient toujours **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Nom du modèle. Cette colonne ne peut pas contenir de valeur **NULL**.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||Type de modèle. Il s'agit d'une chaîne spécifique au fournisseur. Sa valeur peut être **NULL**.|  
|**MODEL_GUID**|**DBTYPE_GUID**||GUID qui identifie le modèle. Les fournisseurs qui n'utilisent pas de GUID pour identifier les tables retournent **NULL**.|  
|**MODEL_PMML**|**DBTYPE_WSTR**||Représentation XML du contenu du modèle au format PMML.|  
|**TAILLE**|**DBTYPE_UI4**||Nombre d'octets dans la chaîne XML.|  
|**EMPLACEMENT**|**DBTYPE_WSTR**||Emplacement du fichier XML. La valeur est **NULL** si un fichier physique n'est pas utilisé pour le stockage.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes DMSCHEMA_MINING_MODEL_XML peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_W**STR|Ce paramètre est facultatif.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma d’exploration de données](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
