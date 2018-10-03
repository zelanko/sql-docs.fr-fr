---
title: La mise à jour des données dans les ensembles de lignes | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f68e4f2be641d6c6aeaf8bbbfcc8cad81ab1a39a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130978"
---
# <a name="updating-data-in-rowsets"></a>Mise à jour des données dans les ensembles de lignes
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mises à jour du fournisseur OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données lorsqu’un consommateur met à jour un ensemble de lignes modifiable qui contient les données. Un ensemble de lignes modifiable est créé lorsque le consommateur demande la prise en charge de l’interface **IRowsetChange** ou **IRowsetUpdate**.  
  
 Tous les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent des ensembles de lignes modifiable par le fournisseur OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les curseurs pour prendre en charge l’ensemble de lignes. La propriété d'ensemble de lignes DBPROP_LOCKMODE modifie le comportement du contrôle concurrentiel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des curseurs et détermine le comportement de l'extraction de lignes d'un ensemble de lignes et la génération d'erreurs d'intégrité des données dans les ensembles de lignes pouvant être mis à jour.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge la synchronisation de lignes avant ou après une mise à jour.  
  
> [!NOTE]  
>  IRowChange::SetColumns permet de définir les valeurs d'une ou de plusieurs colonnes nommées d'un objet ligne.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mise à jour des données dans les curseurs SQL Server](updating-data-in-sql-server-cursors.md)  
  
-   [Resynchronisation des lignes](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  
