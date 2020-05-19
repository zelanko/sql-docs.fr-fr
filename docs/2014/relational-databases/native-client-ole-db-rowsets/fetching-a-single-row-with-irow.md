---
title: Extraction d’une seule ligne avec IRow | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d47e668a2c31e9fb00a8f3582a3538fa9127ef65
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82694656"
---
# <a name="fetching-a-single-row-with-irow"></a>Extraction d'une ligne unique avec IRow
  L’implémentation de l’interface **IRow** dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client est simplifiée pour améliorer les performances. **IRow** autorise l’accès direct aux colonnes d’un objet ligne unique. Si vous savez à l’avance que le résultat d’une exécution de commande produira une ligne exactement, **IRow** récupèrera les colonnes de cette ligne. Si le jeu de résultats comprend plusieurs lignes, **IRow** exposera uniquement la première ligne.  
  
 L’implémentation **IRow** ne permet aucune navigation de la ligne. Chaque colonne dans la ligne est accédée une seule fois, à une exception près : une colonne peut être accédée une fois pour rechercher la taille de colonne et une autre fois pour extraire les données.  
  
> [!NOTE]  
>  **IRow::Open** prend uniquement en charge l’ouverture des types d’objets DBGUID_STREAM et DBGUID_NULL.  
  
 Pour obtenir un objet ligne à l’aide de la méthode **ICommand::Execute**, IID_IRow doit être passé. L’interface **IMultipleResults** doit être utilisée pour gérer plusieurs jeux de résultats. **IMultipleResults** prend en charge **IRow** et **IRowset**. **IRowset** est utilisé pour les opérations en bloc.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d'IRow::GetColumns](using-irow-getcolumns.md)  
  
-   [Extraction de données BLOB à l'aide d'IRow](../../database-engine/dev-guide/fetching-blob-data-using-irow.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  
