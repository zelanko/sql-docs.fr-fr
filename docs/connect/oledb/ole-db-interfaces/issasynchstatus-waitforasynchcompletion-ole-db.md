---
title: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB) | Documents Microsoft
description: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
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
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
apitype: COM
helpviewer_keywords:
- WaitForAsynchCompletion method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 7279c4ca68ddf57824a68cb803cbc5d566ad14b4
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689202"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Attend que l'opération s'exécutant de façon asynchrone se termine ou qu'un délai d'expiration soit dépassé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT WaitForAsynchCompletion(   
        DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *dwMillisecTimeOut*[in]  
 Délai en millisecondes.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 S_OK  
  
 E_UNEXPECTED  
 Un ensemble de lignes est dans un état inutilisé, car **ITransaction::Commit** ou **ITransaction::Abort** a été appelé ou l’ensemble de lignes a été annulé pendant sa phase d’initialisation.  
  
 DB_E_CANCELED  
 Le traitement asynchrone a été annulé pendant l’ensemble de lignes du remplissage ou données source l’initialisation d’objet.  
  
 DB_S_ASYNCHRONOUS  
 L'opération n'est pas encore terminée même si le délai d'expiration spécifié a été atteint.  
  
> [!NOTE]  
>  Outre les valeurs de code de retour répertoriées ci-dessus, la méthode **ISSAsynchStatus::WaitForAsynchCompletion** prend également en charge les valeurs de code de retour retournées par les méthodes OLEDB **ICommand::Execute** et **IDBInitialize::Initialize** principales.  
  
## <a name="remarks"></a>Notes  
 La méthode **ISSAsynchStatus::WaitForAsynchCompletion** n'est pas retournée tant que la valeur du délai d'attente (en millisecondes) n'est pas passée ou que l'opération en attente n'est pas terminée. L'objet **Command** a une propriété **CommandTimeout** qui contrôle le nombre de secondes pendant lesquelles une requête doit s'exécuter avant l'expiration du délai imparti. Le **CommandTimeout** propriété sera ignorée si utilisée avec **ISSAsynchStatus::WaitForAsynchCompletion** (méthode).  
  
 La propriété relative au délai d'expiration est ignorée pour les opérations asynchrones. Le paramètre de délai d'expiration de **ISSAsynchStatus::WaitForAsynchCompletion** spécifie la durée maximale qui doit s'écouler avant que le contrôle ne soit retourné à l'appelant. Si ce délai expire, DB_S_ASYNCHRONOUS est retourné. L'expiration des délais d'attente n'annule jamais les opérations asynchrones. Si l'application doit annuler une opération asynchrone qui ne se termine pas dans un délai imparti, elle doit attendre l'expiration du délai, puis annuler explicitement l'opération si DB_S_ASYNCHRONOUS est retourné.  
  
> [!NOTE]  
>  Lorsque les composants du Service OLE DB sont utilisés, S_OK peut être retourné lorsque DB_S_ASYNCHRONOUS est attendu, les applications doivent appeler [ISSAsynchStatus::GetStatus](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) à vérifier pour achèvement lorsque S_OK ou DB_S_ASYNCHRONOUS est retourné.  
  
 Si la valeur de *dwMillisecTimeOut* est INFINITE, la méthode **ISSAsynchStatus::WaitForAsynchCompletion** se bloque jusqu'à ce que l'opération soit terminée. Si la valeur de *dwMillisecTimeOut* est 0, la méthode est retournée immédiatement avec l'état de l'opération en attente. Si le délai d’attente expire avant que l’opération soit terminée, DB_S_ASYNCHRONOUS est retourné.  
  
 Si l'opération se termine avant l'expiration du délai d'attente, le HRESULT retourné correspond au HRESULT retourné par l'opération (HRESULT retourné si l'opération était effectuée de façon synchrone).  
  
 De plus, la propriété SSPROP_ISSAsynchStatus a été ajoutée au jeu de propriétés DBPROPSET_SQLSERVERROWSET. Les fournisseurs qui prennent en charge la [ISSAsynchStatus](../../oledb/ole-db-interfaces/issasynchstatus-ole-db.md) interface doit implémenter cette propriété avec la valeur VARIANT_TRUE.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations asynchrones](../../oledb/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
