---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d66d37da3ba2de7f12cefb8f806c44d5dd967003
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73763176"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Annule l'ensemble de lignes actuel plus toutes les commandes par lot associées à la commande actuelle.  
  
L'interface **ISSAbort** , exposée dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, fournit la méthode **ISSAbort::Abort** utilisée pour annuler l'ensemble de lignes actuel, plus les commandes regroupées par lot avec la commande ayant généré initialement l'ensemble de lignes et dont l'exécution n'est pas encore achevée.  
  
 **Méthode ISSAbort** est une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interface propre au fournisseur native client disponible en utilisant **QueryInterface** sur l’objet **IMultipleResults** retourné par **ICommand :: Execute** ou **IOpenRowset :: OpenRowset**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Notes  
 Si la commande abandonnée se trouve dans une procédure stockée, l'exécution de la procédure stockée (et de toutes les procédures ayant appelé cette procédure) sera annulée, tout comme le lot de commandes contenant l'appel de procédure stockée. Si le serveur est en cours de transfert d'un jeu de résultats vers le client, cette opération sera arrêtée. Si le client ne souhaite pas consommer un jeu de résultats, l'appel de la méthode **ISSAbort::Abort** avant la diffusion de l'ensemble de lignes permettra d'accélérer cette dernière. En revanche, si une transaction est ouverte et si XACT_ABORT est défini sur ON (c'est-à-dire activé), la transaction sera restaurée lors de l'appel de la méthode **ISSAbort::Abort** .  
  
 Dès que **ISSAbort::Abort** retourne S_OK, l'interface **IMultipleResults** associée adopte un état inutilisable et retourne DB_E_CANCELED à tous les appels de méthode (sauf pour les méthodes définies par l'interface **IUnknown** ) jusqu'à ce qu'elle soit diffusée. Si une interface **IRowset** a été obtenue à partir de l'interface **IMultipleResults** avant un appel à **à Abort**, elle adopte également un état inutilisable et retourne DB_E_CANCELED à tous les appels de méthode (sauf pour les méthodes définies par l'interface **IUnknown** et **IRowset::ReleaseRows**) jusqu'à ce qu'elle soit diffusée après l'appel en bonne et due forme de la méthode **ISSAbort::Abort**.  
  
> [!NOTE]  
>  À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], si l’état XACT_ABORT du serveur est défini sur ON, l’exécution de la méthode **ISSAbort::Abort** prend fin et restaure toutes les transactions implicites ou explicites actuelles lors de la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'abandonneront pas la transaction actuelle.  
  
## <a name="arguments"></a>Arguments  
 Aucun.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 La méthode **ISSAbort::Abort** retourne S_OK si le lot a été annulé ou bien DB_E_CANTCANCEL dans le cas inverse. Si le lot a déjà été annulé, DB_E_CANCELED est retourné.  
  
 DB_E_CANCELED  
 Le lot a déjà été annulé.  
  
 DB_E_CANTCANCEL  
 Le lot n'a pas été annulé.  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s’est produite ; Pour plus d’informations, utilisez l’interface [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) .  
  
 E_UNEXPECTED  
 L'appel à la méthode était inattendu. Par exemple, l'objet est dans un état zombie parce que la méthode **ISSAbort::Abort** a déjà été appelée.  
  
 E_OUTOFMEMORY  
 Erreur de mémoire insuffisante.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode ISSAbort &#40;OLE DB&#41;](https://msdn.microsoft.com/library/7c4df482-4a83-4da0-802b-3637b507693a)  
  
  
