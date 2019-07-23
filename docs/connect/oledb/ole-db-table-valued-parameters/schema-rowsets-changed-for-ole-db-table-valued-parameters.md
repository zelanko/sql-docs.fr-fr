---
title: Ensembles de lignes de schéma modifiés pour les paramètres table OLE DB | Microsoft Docs
description: Ensembles de lignes de schéma modifiés pour les paramètres table OLE DB
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0ca6d03779f58719d1b56e8d3de9e45bfa3a36c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015299"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>Ensembles de lignes de schéma modifiés pour les paramètres table OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le tableau suivant répertorie les ensembles de lignes de schéma qui ont été modifiés ou ajoutés pour prendre en charge des paramètres table.  
  
|Ensemble de lignes de schéma|Description|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Deux nouvelles colonnes ont été ajoutées à la fin de l'ensemble de lignes nommé SS_TYPE_CATALOG_NAME et SS_TYPE_SCHEMANAME. Ces colonnes peuvent être réutilisées pour des types futurs. Les colonnes TYPE_NAME et LOCAL_TYPE_NAME contiendront le nom du type TABLE de paramètre table. La colonne DATA_TYPE aura la valeur DBTYPE_TABLE = 143 pour les paramètres table.|  
|DBSCHEMA_TABLE_TYPES|Cet ensemble de lignes a été ajouté pour prendre en charge des paramètres table. Il est identique à DBSCHEMA_TABLES, à la différence près qu'il retourne uniquement des métadonnées pour des types de table plutôt que pour des tables, des vues ou des synonymes. La colonne TABLE_TYPE aura la valeur « TABLE TYPE ».|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|Cet ensemble de lignes a été ajouté pour prendre en charge des paramètres table. Il est identique à DBSCHEMA_PRIMARY_KEYS, à la différence près qu'il retourne uniquement des métadonnées de clés primaires pour des types de table plutôt que pour des tables.|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|Cet ensemble de lignes a été ajouté pour prendre en charge des paramètres table. Il est identique à DBSCHEMA_COLUMNS, à la différence près qu'il retourne uniquement des métadonnées de colonne pour des types de table plutôt que pour des tables, des vues ou des synonymes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
