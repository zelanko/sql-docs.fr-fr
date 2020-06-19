---
title: Méthode ISSAbort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7195311fefe3f0f1b7b4d6d789aa8d8487bc3bfe
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933500"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  L'interface **ISSAbort** , exposée dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, fournit la méthode [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) utilisée pour annuler l'ensemble de lignes actuel, plus les commandes regroupées par lot avec la commande ayant généré initialement l'ensemble de lignes et dont l'exécution n'est pas encore achevée.  
  
 **ISSAbort** est une interface propre au fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client disponible en utilisant **QueryInterface** sur l'objet **IMultipleResults** retourné par **ICommand::Execute** ou **IOpenRowset::OpenRowset**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode ISSAbort :: Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|Annule l'ensemble de lignes actuel plus toutes les commandes par lot associées à la commande actuelle.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
