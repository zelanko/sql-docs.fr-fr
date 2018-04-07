---
title: Signets | Documents Microsoft
description: Signets dans le pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- OLE DB Driver for SQL Server, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bfca58f2db78257921f9f6864a7b8325f86c7705
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="bookmarks"></a>Signets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les signets permettent aux consommateurs de revenir rapidement à une ligne. Avec les signets, les consommateurs peuvent accéder aléatoirement aux lignes selon la valeur du signet. La colonne du signet est la colonne 0 dans l'ensemble de lignes. Le consommateur attribue la valeur de champ dwFlag de la structure de liaison à DBCOLUMNSINFO_ISBOOKMARK pour indiquer que la colonne est utilisée comme signet. Le consommateur définit également la propriété d'ensemble de lignes DBPROP_BOOKMARKS avec la valeur VARIANT_TRUE. La colonne 0 peut ainsi être présente dans l'ensemble de lignes. Le **IRowsetLocate::GetRowsAt** méthode est ensuite utilisée pour extraire les lignes, en commençant par la ligne spécifiée en tant que décalage à partir d’un signet.  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
