---
title: Extraction d’une ligne unique avec IRow | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 243d57b5e42e2c4ecebec6ce1e05d3061baa0a2c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412398"
---
# <a name="fetching-a-single-row-with-irow"></a>Extraction d'une ligne unique avec IRow
  Le **IRow** interface d’implémentation dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif est simplifié pour améliorer les performances. **IRow** permet un accès direct aux colonnes d’un objet ligne unique. Si vous connaissez au préalable que le résultat d’une exécution de la commande génère une ligne exactement, **IRow** extraira les colonnes de cette ligne. Si le jeu de résultats comprend plusieurs lignes, **IRow** exposera uniquement la première ligne.  
  
 Le **IRow** implémentation n’autorise aucune navigation de la ligne. Chaque colonne dans la ligne est accédée une seule fois, à une exception près : une colonne peut être accédée une fois pour rechercher la taille de colonne et une autre fois pour extraire les données.  
  
> [!NOTE]  
>  **IRow::Open** prend en charge le seul type DBGUID_STREAM et DBGUID_NULL d’objets à ouvrir.  
  
 Pour obtenir un objet de ligne à l’aide **ICommand::Execute** (méthode), IID_IRow doit être passé. Le **IMultipleResults** interface doit être utilisée pour gérer plusieurs jeux de résultats. **IMultipleResults** prend en charge **IRow** et **IRowset**. **IRowset** est utilisé pour les opérations en bloc.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d’IRow::GetColumns](using-irow-getcolumns.md)  
  
-   [Extraction de données Blob à l’aide d’IRow](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  
