---
title: Ensemble de lignes MDSCHEMA_MEASUREGROUPS | Documents Microsoft
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
- MDSCHEMA_MEASUREGROUPS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 046674dc7c579a99e3d9fd90a86c466001c270c0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051363"
---
# <a name="mdschemameasuregroups-rowset"></a>Ensemble de lignes MDSCHEMA_MEASUREGROUPS
  Décrit les groupes de mesures d'une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_MEASUREGROUPS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom du catalogue auquel appartient ce groupe de mesures. Valeur `NULL` si le fournisseur ne prend pas en charge les catalogues.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube auquel appartient ce groupe de mesures.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Nom du groupe de mesures.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description du membre à l'intention des utilisateurs.|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||Valeur booléenne indiquant si le groupe de mesures est activé en écriture.<br /><br /> Retourne `true` si le groupe de mesures est activé en écriture.|  
|`MEASUREGROUP_CAPTION`|`DBTYPE_WSTR`||Légende d'affichage pour le groupe de mesures.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes `MDSCHEMA_MEASUREGROUPS` peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  