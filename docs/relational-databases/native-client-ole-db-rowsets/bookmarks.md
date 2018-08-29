---
title: Signets | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c9e96fe0355cde4e7cd408a69f81da9b3bde0f95
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43099554"
---
# <a name="bookmarks"></a>Signets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les signets permettent aux consommateurs de revenir rapidement à une ligne. Avec les signets, les consommateurs peuvent accéder aléatoirement aux lignes selon la valeur du signet. La colonne du signet est la colonne 0 dans l'ensemble de lignes. Le consommateur attribue la valeur de champ dwFlag de la structure de liaison à DBCOLUMNSINFO_ISBOOKMARK pour indiquer que la colonne est utilisée comme signet. Le consommateur définit également la propriété d'ensemble de lignes DBPROP_BOOKMARKS avec la valeur VARIANT_TRUE. La colonne 0 peut ainsi être présente dans l'ensemble de lignes. Puis, la méthode **IRowsetLocate::GetRowsAt** est utilisée pour récupérer (fetch) les lignes, en commençant par la ligne spécifiée comme offset d’un signet.  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
