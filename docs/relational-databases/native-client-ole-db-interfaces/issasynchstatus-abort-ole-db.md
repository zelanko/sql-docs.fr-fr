---
description: 'ISSAsynchStatus :: Abort (fournisseur Native Client OLE DB)'
title: 'ISSAsynchStatus :: Abort (fournisseur Native Client OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 39453e5f06b2702b171d639cc6989dd1d9aaf3b4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469390"
---
# <a name="issasynchstatusabort-native-client-ole-db-provider"></a>ISSAsynchStatus :: Abort (fournisseur Native Client OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Annule une opération s'exécutant de manière asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT Abort(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>Arguments  
 *hChapter*[in]  
 Handle du chapitre pour lequel vous souhaitez abandonner l'opération. Si l'objet appelé n'est pas un objet d'ensemble de lignes ou que l'opération ne s'applique pas à un chapitre, l'appelant doit attribuer la valeur DB_NULL_HCHAPTER à *hChapter* .  
  
 *eOperation*[in]  
 L'opération à abandonner. Elle doit avoir la valeur suivante :  
  
 DBASYNCHOP_OPEN : la demande d'annulation s'applique à l'ouverture ou au remplissage asynchrone d'un ensemble de lignes ou à l'initialisation asynchrone d'un objet source de données.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 La demande d'annulation de l'opération asynchrone a été traitée. Cela ne garantit pas que l'opération ait été annulée. Pour déterminer si l'opération a bien été annulée, le consommateur doit appeler [ISSAsynchStatus::GetStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) et vérifier la présence de DB_E_CANCELED ; toutefois, il est possible qu'il ne soit pas retourné dans l'appel suivant.  
  
 DB_E_CANTCANCEL  
 L'opération asynchrone ne peut pas être annulée.  
  
 DB_E_CANCELED  
 La demande d'abandon de l'opération asynchrone a été annulée au cours de notifications. L'opération est encore exécutée de manière asynchrone.  
  
 E_FAIL  
 Une erreur spécifique au fournisseur s'est produite.  
  
 E_INVALIDARG  
 Le paramètre *hChapter* n'est pas DB_NULL_HCHAPTER ou *eOperation* n'est pas DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 **ISSAsynchStatus::Abort** a été appelé sur un objet source de données sur lequel **IDBInitialize::Initialize** n'a pas été appelé ou ne s'est pas terminé.  
  
 **ISSAsynchStatus::Abort** a été appelé sur un objet source de données sur lequel **IDBInitialize::Initialize** a été appelé mais a été par la suite annulé avant l'initialisation ou a dépassé le délai d'attente. L'objet source de données n'est pas encore initialisé.  
  
 **ISSAsynchStatus::Abort** a été appelé sur un ensemble de lignes sur lequel **ITransaction::Commit** ou **ITransaction::Abort** a été appelé précédemment, et l'ensemble de lignes n'a pas survécu à la validation ou à l'abandon et se trouve dans un état passif.  
  
 **ISSAsynchStatus::Abort** a été appelé sur un ensemble de lignes qui a été annulé de manière asynchrone dans sa phase d'initialisation. L'ensemble de lignes se trouve dans un état zombie.  
  
## <a name="remarks"></a>Notes  
 L'abandon de l'initialisation d'un ensemble de lignes ou d'un objet source de données peut laisser l'ensemble de lignes ou l'objet source de données dans un état zombie, de telle sorte que toutes les méthodes autres que **IUnknown** retournent E_UNEXPECTED. Lorsque cela se produit, la seule action possible pour le consommateur est de libérer l'ensemble de lignes ou l'objet source de données.  
  
 Le fait d'appeler **ISSAsynchStatus::Abort** et de passer une valeur pour *eOperation* autre que DBASYNCHOP_OPEN retourne S_OK. Cela ne signifie pas pour autant que l'opération est terminée ou annulée.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations asynchrones](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
