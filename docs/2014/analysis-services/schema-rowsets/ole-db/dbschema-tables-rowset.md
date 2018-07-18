---
title: Ensemble de lignes DBSCHEMA_TABLES | Microsoft Docs
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
- DBSCHEMA_TABLES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_TABLES rowset
ms.assetid: 14c16e6b-0aff-4ad1-b98f-cdb7df0f8d73
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 83537dc9159331342ae344e5003d9c04fd8980eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211829"
---
# <a name="dbschematables-rowset"></a>Ensemble de lignes DBSCHEMA_TABLES
  Identifie les groupes de mesures et les dimensions exposés en tant que tables dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DBSCHEMA_TABLES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|255|Nom du catalogue auquel appartient cet objet.|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|255|Nom du cube auquel appartient cet objet.|  
|`TABLE_NAME`|`DBTYPE_WSTR`|255|Nom de l'objet, si `TABLE_TYPE` est `TABLE`.|  
|`TABLE_TYPE`|`DBTYPE_WSTR`||Type de la table.<br /><br /> `TABLE` Indique l’objet est un groupe de mesures.<br /><br /> `SYSTEM TABLE` Indique l’objet est une dimension.|  
|`TABLE_GUID`|`DBTYPE_GUID`||Non pris en charge.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description de l'objet à l'intention des utilisateurs.|  
|`TABLE_PROPID`|`DBTYPE_UI4`||Non pris en charge.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Non pris en charge.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Date de la dernière modification de l'objet.|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`||Type OLAP de l'objet.<br /><br /> **Groupe_mesure** indique l’objet est un groupe de mesures.<br /><br /> `CUBE_DIMENSION` indique que l'objet est une dimension.|  
  
 L'ensemble de lignes est trié selon `TABLE_TYPE`, `TABLE_CATALOG`, `TABLE_SCHEMA` et `TABLE_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DBSCHEMA_TABLES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`TABLE_CATALOG`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`TABLE_SCHEMA`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`TABLE_NAME`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`TABLE_TYPE`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
|`TABLE_OLAP_TYPE`|`DBTYPE_WSTR`|Ce paramètre est facultatif|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB](ole-db-schema-rowsets.md)  
  
  
