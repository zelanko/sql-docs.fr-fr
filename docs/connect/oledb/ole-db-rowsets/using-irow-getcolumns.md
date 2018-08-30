---
title: Utilisation d’IRow::GetColumns | Microsoft Docs
description: À l’aide d’IRow::GetColumns pour accéder à toutes les colonnes dans une ligne
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- GetColumns method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: b92b76eca593259457727f9f870eb45b66cb477d
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025757"
---
# <a name="using-irowgetcolumns"></a>Utilisation d'IRow::GetColumns
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L’implémentation **IRow** permet un accès séquentiel de type « avant uniquement » aux colonnes. Vous pouvez accéder à toutes les colonnes d’une ligne avec un appel unique à **IRow::GetColumns**, ou appeler **IRow::GetColumns** chaque fois que vous accédez à plusieurs colonnes de la ligne.  
  
 Les appels multiples à **IRow::GetColumns** ne doivent pas se chevaucher. Par exemple, si le premier appel à **IRow::GetColumns** récupère les données des colonnes 1, 2 et 3, le deuxième appel à **IRow::GetColumns** doit appeler les colonnes 4, 5 et 6. Si des appels ultérieurs à **IRow::GetColumns** se chevauchent, l’indicateur d’état (champ dwstatus dans DBCOLUMNACCESS) a la valeur DBSTATUS_E_UNAVAILABLE.  
  
## <a name="see-also"></a> Voir aussi  
 [Récupération d’une ligne unique avec IRow](../../oledb/ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
  
