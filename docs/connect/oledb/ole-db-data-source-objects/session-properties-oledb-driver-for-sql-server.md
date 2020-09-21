---
title: Propriétés de session - Pilote OLE DB pour SQL Server | Microsoft Docs
description: Découvrez comment OLE DB Driver pour SQL Server interprète les propriétés de session OLE DB, y compris un jeu de propriétés spécifiques au fournisseur.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6e3eba687afbf9b981d19a40a52d259bb43daa7
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862044"
---
# <a name="session-properties---ole-db-driver-for-sql-server"></a>Propriétés de session - OLE DB Driver pour SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le fournisseur OLE DB Driver pour SQL Server interprète les propriétés de la session OLE DB comme suit.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Le pilote OLE DB pour SQL Server prend en charge tous les niveaux d’isolation des transactions de validation automatique, à l’exception du niveau de chaos DBPROPVAL_TI_CHAOS.|  
  
 Dans le jeu de propriétés DBPROPSET_SQLSERVERSESSION spécifique au fournisseur, le pilote OLE DB pour SQL Server définit la propriété de session supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Type : VT_BOOL<br /><br /> R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : identificateurs entre guillemets autorisés dans la restriction CATALOG.<br /><br /> VARIANT_TRUE : les identificateurs entre guillemets sont reconnus pour une restriction de catalogue pour les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées.<br /><br /> VARIANT_FALSE : les identificateurs entre guillemets ne sont pas reconnus pour une restriction de catalogue pour les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées.<br /><br /> Pour plus d’informations sur les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées, consultez [Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma](../../oledb/ole-db/schema-rowsets-distributed-query-support.md).|  
|SSPROP_ALLOWNATIVEVARIANT|Type : VT_BOOL<br /><br /> Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : détermine si les données sont extraites en tant que DBTYPE_VARIANT ou DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE : le type de colonne est retourné en tant que DBTYPE_SQLVARIANT, auquel cas la mémoire tampon contient la structure SSVARIANT.<br /><br /> VARIANT_FALSE : le type de colonne est retourné en tant que DBTYPE_VARIANT et la mémoire tampon a la structure VARIANT.|  
|SSPROP_ASYNCH_BULKCOPY|Pour utiliser le mode asynchrone, affectez la valeur VARIANT_TRUE à la propriété de session spécifique au fournisseur SSPROP_ASYNCH_BULKCOPY avant d'appeler la méthode BCPExec. Cette propriété est disponible dans le jeu de propriétés DBPROPSET_SQLSERVERSESSION.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets source de données &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
