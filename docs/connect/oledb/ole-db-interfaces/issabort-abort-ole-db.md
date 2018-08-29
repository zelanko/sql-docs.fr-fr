---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
description: ISSAbort::Abort (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9d838ad97c863670a5474cd08e626e7d4c0faf36
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43035555"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Annule l'ensemble de lignes actuel plus toutes les commandes par lot associées à la commande actuelle.  
  
L’interface **ISSAbort**, qui est exposée dans le pilote OLE DB pour SQL Server, fournit la méthode **ISSAbort::Abort** utilisée pour annuler l’ensemble de lignes actuel, plus les commandes regroupées par lot avec la commande ayant généré initialement l’ensemble de lignes et dont l’exécution n’est pas encore achevée.  
  
 **ISSAbort** est une interface propre au pilote OLE DB pour SQL Server disponible en utilisant **QueryInterface** sur l’objet **IMultipleResults** retourné par **ICommand::Execute** ou **IOpenRowset::OpenRowset**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Notes   
 Si la commande abandonnée se trouve dans une procédure stockée, l’exécution de la procédure stockée (et de toutes les procédures ayant appelé cette procédure) sera annulée, tout comme le lot de commandes contenant l’appel de procédure stockée. Si le serveur est occupé à transférer un jeu de résultats vers le client, cette opération sera arrêtée. Si le client ne souhaite pas consommer un jeu de résultats, l'appel de la méthode **ISSAbort::Abort** avant la diffusion de l'ensemble de lignes permettra d'accélérer cette dernière. En revanche, si une transaction est ouverte et si XACT_ABORT est défini sur ON (c'est-à-dire activé), la transaction sera restaurée lors de l'appel de la méthode **ISSAbort::Abort** .  
  
 Une fois que **ISSAbort::Abort** a retourné S_OK, l’interface **IMultipleResults** associée entre dans un état inutilisable et retourne DB_E_CANCELED à tous les appels de méthode (sauf pour les méthodes définies par l’interface **IUnknown**) jusqu’à ce qu’elle soit libérée. Si une interface **IRowset** a été obtenue à partir de l'interface **IMultipleResults** avant un appel à **à Abort**, elle adopte également un état inutilisable et retourne DB_E_CANCELED à tous les appels de méthode (sauf pour les méthodes définies par l'interface **IUnknown** et **IRowset::ReleaseRows**) jusqu'à ce qu'elle soit diffusée après l'appel en bonne et due forme de la méthode **ISSAbort::Abort**.  
  
> [!NOTE]  
>  À compter de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], si l’état XACT_ABORT du serveur est défini sur ON, l’exécution de la méthode **ISSAbort::Abort** prend fin et restaure toutes les transactions implicites ou explicites actuelles lors de la connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'abandonneront pas la transaction actuelle.  
  
## <a name="arguments"></a>Arguments  
 Aucun.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 La méthode **ISSAbort::Abort** retourne S_OK si le lot a été annulé ou bien DB_E_CANTCANCEL dans le cas inverse. Si le lot a déjà été annulé, DB_E_CANCELED est retourné.  
  
 DB_E_CANCELED  
 Le lot a déjà été annulé.  
  
 DB_E_CANTCANCEL  
 Le lot n'a pas été annulé.  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite. Pour obtenir des informations détaillées, utilisez l’interface [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, l'objet est dans un état zombie parce que la méthode **ISSAbort::Abort** a déjà été appelée.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
  
