---
title: Signets | Microsoft Docs
description: Les signets dans OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- OLE DB Driver for SQL Server, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 228aef19efd1efd6ffa2c189094d20daf35fe1d4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597310"
---
# <a name="bookmarks"></a>Signets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les signets permettent aux consommateurs de revenir rapidement à une ligne. Avec les signets, les consommateurs peuvent accéder aléatoirement aux lignes selon la valeur du signet. La colonne du signet est la colonne 0 dans l'ensemble de lignes. Le consommateur attribue la valeur de champ dwFlag de la structure de liaison à DBCOLUMNSINFO_ISBOOKMARK pour indiquer que la colonne est utilisée comme signet. Le consommateur définit également la propriété d'ensemble de lignes DBPROP_BOOKMARKS avec la valeur VARIANT_TRUE. La colonne 0 peut ainsi être présente dans l'ensemble de lignes. Puis, la méthode **IRowsetLocate::GetRowsAt** est utilisée pour récupérer (fetch) les lignes, en commençant par la ligne spécifiée comme offset d’un signet.  
  
## <a name="see-also"></a> Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
