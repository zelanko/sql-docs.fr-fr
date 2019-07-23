---
title: Extraction d’une seule ligne avec IRow | Microsoft Docs
description: Extraction d’une seule ligne à l’aide de l’interface IRow du pilote OLE DB pour SQL Server
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
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 542875dc322cd94970c238747db0adb139b9a480
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994295"
---
# <a name="fetching-a-single-row-with-irow"></a>Extraction d'une ligne unique avec IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L’implémentation de l’interface **IRow** dans le pilote OLE DB pour SQL Server est simplifiée pour améliorer les performances. **IRow** autorise l’accès direct aux colonnes d’un objet ligne unique. Si vous savez à l’avance que le résultat d’une exécution de commande produira une ligne exactement, **IRow** récupèrera les colonnes de cette ligne. Si le jeu de résultats comprend plusieurs lignes, **IRow** exposera uniquement la première ligne.  
  
 L’implémentation **IRow** ne permet aucune navigation de la ligne. Chaque colonne dans la ligne est accédée une seule fois, à une exception près : une colonne peut être accédée une fois pour rechercher la taille de colonne et une autre fois pour extraire les données.  
  
> [!NOTE]  
>  **IRow::Open** prend uniquement en charge l’ouverture des types d’objets DBGUID_STREAM et DBGUID_NULL.  
  
 Pour obtenir un objet ligne à l’aide de la méthode **ICommand::Execute**, IID_IRow doit être passé. L’interface **IMultipleResults** doit être utilisée pour gérer plusieurs jeux de résultats. **IMultipleResults** prend en charge **IRow** et **IRowset**. **IRowset** est utilisé pour les opérations en bloc.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d’IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
