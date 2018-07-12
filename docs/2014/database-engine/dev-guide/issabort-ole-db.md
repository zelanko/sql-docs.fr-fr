---
title: ISSAbort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
caps.latest.revision: 11
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace6518c1a0f4ece66ec0b9b24cb9e109db7ffa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180346"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  Le **ISSAbort** interface, ce qui est exposé dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client, fournit le [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) méthode qui est utilisée pour annuler l’ensemble de lignes actuel plus toutes les commandes par lot avec la commande ayant généré initialement l’ensemble de lignes, et qui n’ont pas encore terminée l’exécution.  
  
 **ISSAbort** est un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interface propre au fournisseur de Native Client disponible à l’aide de **QueryInterface** sur le **IMultipleResults** objet retourné par  **ICommand::Execute** ou **IOpenRowset::OpenRowset**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISSAbort::Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Annule l'ensemble de lignes actuel plus toutes les commandes par lot associées à la commande actuelle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
