---
title: ISSAbort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4b3e43dca5a18a991733492eeeffc4f49d14ef8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181239"
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
  
  
