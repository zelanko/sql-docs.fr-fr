---
title: Ensemble de lignes DBSCHEMA_TABLES | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBSCHEMA_TABLES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e823aca2ca72fe756fe41cabf49fe61f26cec106
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="dbschematables-rowset"></a>Ensemble de lignes DBSCHEMA_TABLES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Identifie les groupes de mesures et les dimensions exposés en tant que tables dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **DBSCHEMA_TABLES** ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|255|Nom du catalogue auquel appartient cet objet.|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|255|Nom du cube auquel appartient cet objet.|  
|**NOM_TABLE**|**DBTYPE_WSTR**|255|Le nom de l’objet, si **TABLE_TYPE** est **TABLE**.|  
|**TABLE_TYPE**|**DBTYPE_WSTR**||Type de la table.<br /><br /> **TABLE** indique l’objet est un groupe de mesures.<br /><br /> **TABLE système** indique l’objet est une dimension.|  
|**TABLE_GUID**|**DBTYPE_GUID**||Non pris en charge.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Description de l'objet à l'intention des utilisateurs.|  
|**TABLE_PROPID**|**DBTYPE_UI4**||Non pris en charge.|  
|**DATE_DE_CRÉATION**|**DBTYPE_DBTIMESTAMP**||Non pris en charge.|  
|**DATE_DE_MODIFICATION**|**DBTYPE_DBTIMESTAMP**||Date de la dernière modification de l'objet.|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**||Type OLAP de l'objet.<br /><br /> **Groupe_mesure** indique l’objet est un groupe de mesures.<br /><br /> **CUBE_DIMENSION** indique que l’objet est une dimension.|  
  
 L’ensemble de lignes est trié sur **TABLE_TYPE**, **TABLE_CATALOG**, **TABLE_SCHEMA**, et **TABLE_NAME**.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le **DBSCHEMA_TABLES** ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**TABLE_CATALOG**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
|**TABLE_SCHEMA**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
|**NOM_TABLE**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
|**TABLE_TYPE**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
|**TABLE_OLAP_TYPE**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
