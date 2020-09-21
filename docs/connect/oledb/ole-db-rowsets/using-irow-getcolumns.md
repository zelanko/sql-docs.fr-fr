---
title: Utilisation de IRow::GetColumns (pilote OLE DB)
description: Découvrez comment utiliser IRow::GetColumns pour accéder à toutes les colonnes d’une ligne dans OLE DB Driver pour SQL Server. IRow autorise l’accès séquentiel en avant uniquement aux colonnes.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 60ded2ad36346bcb05d75add252f0357c48398e7
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88859936"
---
# <a name="using-irowgetcolumns"></a>Utilisation d'IRow::GetColumns
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L’implémentation **IRow** permet un accès séquentiel de type « avant uniquement » aux colonnes. Vous pouvez accéder à toutes les colonnes d’une ligne avec un appel unique à **IRow::GetColumns**, ou appeler **IRow::GetColumns** chaque fois que vous accédez à plusieurs colonnes de la ligne.  
  
 Les appels multiples à **IRow::GetColumns** ne doivent pas se chevaucher. Par exemple, si le premier appel à **IRow::GetColumns** récupère les données des colonnes 1, 2 et 3, le deuxième appel à **IRow::GetColumns** doit appeler les colonnes 4, 5 et 6. Si des appels ultérieurs à **IRow::GetColumns** se chevauchent, l’indicateur d’état (champ dwstatus dans DBCOLUMNACCESS) a la valeur DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’une ligne unique avec IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
