---
title: Ensemble de lignes MDSCHEMA_INPUT_DATASOURCES | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6efa6baf40c41db7de09ebcb4e5c44990ff7e6ed
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mdschemainputdatasources-rowset"></a>Ensemble de lignes MDSCHEMA_INPUT_DATASOURCES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Décrit les sources de données définies dans la base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **MDSCHEMA_INPUT_DATASOURCES** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nom du catalogue auquel appartient cette source de données.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Non pris en charge.|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**||Nom de l'objet source de données.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**||Type de la source de données. Les valeurs valides sont les suivantes :<br /><br /> **Relationnelle**<br /><br /> **OLAP**|  
|**CREATED_ON**|**DBTYPE_DBTIMESTAMP**||Date de création de la source de données.|  
|**LAST_SCHEMA_UPDATE**|**DBTYPE_DBTIMESTAMP**||Date et heure de la dernière modification de la source de données.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Description conviviale de l'action.|  
|**DÉLAI D’ATTENTE**|**DBTYPE_UI4**||Délai d'expiration de la source de données.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **MDSCHEMA_INPUT_DATASOURCES** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**DATASOURCE_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**DATASOURCE_TYPE**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [OLE DB pour OLAP Schema Rowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
