---
title: Ensemble de lignes MDSCHEMA_MEASUREGROUPS | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MDSCHEMA_MEASUREGROUPS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 470a0987e6bc23b9b2d85283bfb85866036cec5d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="mdschemameasuregroups-rowset"></a>Ensemble de lignes MDSCHEMA_MEASUREGROUPS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Décrit les groupes de mesures dans une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **MDSCHEMA_MEASUREGROUPS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nom du catalogue auquel appartient ce groupe de mesures. Valeur**NULL** si le fournisseur ne prend pas en charge les catalogues.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Non pris en charge.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Nom du cube auquel appartient ce groupe de mesures.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**||Nom du groupe de mesures.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Description du membre à l'intention des utilisateurs.|  
|**IS_WRITE_ENABLED**|**DBTYPE_BOOL**||Valeur booléenne indiquant si le groupe de mesures est activé en écriture.<br /><br /> Retourne **true** si le groupe de mesures est activé en écriture.|  
|**MEASUREGROUP_CAPTION**|**DBTYPE_WSTR**||Légende d'affichage pour le groupe de mesures.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **MDSCHEMA_MEASUREGROUPS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**MEASUREGROUP_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
