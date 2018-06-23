---
title: ISSAbort (OLE DB) | Documents Microsoft
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 53c6e2c7c06331ce75883f86a8935d4d1c2419c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043413"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  Le **ISSAbort** interface, exposée dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client fournit le [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) méthode qui est utilisée pour annuler l’ensemble de lignes actuel plus toutes les commandes traitées par lot avec la commande ayant généré initialement l’ensemble de lignes, et qui n’ont pas terminé l’exécution.  
  
 **ISSAbort** est un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client interface spécifique au fournisseur disponible à l’aide de **QueryInterface** sur la **IMultipleResults** objet retourné par  **ICommand::Execute** ou **IOpenRowset::OpenRowset**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISSAbort::Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Annule l'ensemble de lignes actuel plus toutes les commandes par lot associées à la commande actuelle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  