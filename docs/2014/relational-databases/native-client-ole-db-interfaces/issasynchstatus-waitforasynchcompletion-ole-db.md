---
title: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af77f5f5519a49e2d9a744dceca2857cc88ce8e1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63192312"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
  Attend que l'opération s'exécutant de façon asynchrone se termine ou qu'un délai d'expiration soit dépassé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
HRESULT WaitForAsynchCompletion(   
  DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *dwMillisecTimeOut*[in]  
 Délai en millisecondes.  
  
## <a name="return-code-values"></a>Codet de retour  
 S_OK  
 S_OK  
  
 E_UNEXPECTED  
 Un ensemble de lignes est dans un état inutilisé, car **ITransaction::Commit** ou **ITransaction::Abort** a été appelé, ou l'ensemble de lignes a été annulé pendant sa phase d'initialisation.  
  
 DB_E_CANCELED  
 Le traitement asynchrone a été annulé pendant le remplissage de l'ensemble de lignes ou l'initialisation de l'objet source de données.  
  
 DB_S_ASYNCHRONOUS  
 L'opération n'est pas encore terminée même si le délai d'expiration spécifié a été atteint.  
  
> [!NOTE]  
>  Outre les valeurs de code de retour répertoriées ci-dessus, la méthode **ISSAsynchStatus::WaitForAsynchCompletion** prend également en charge les valeurs de code de retour retournées par les méthodes OLEDB **ICommand::Execute** et **IDBInitialize::Initialize** principales.  
  
## <a name="remarks"></a>Notes  
 La méthode **ISSAsynchStatus::WaitForAsynchCompletion** n'est pas retournée tant que la valeur du délai d'attente (en millisecondes) n'est pas passée ou que l'opération en attente n'est pas terminée. L’objet **Command** a une propriété **CommandTimeout** qui contrôle le nombre de secondes pendant lesquelles une requête doit s’exécuter avant l’expiration du délai d’attente. La propriété **CommandTimeout** est ignorée si elle est utilisée conjointement avec la méthode **ISSAsynchStatus :: WaitForAsynchCompletion** .  
  
 La propriété relative au délai d'expiration est ignorée pour les opérations asynchrones. Le paramètre de délai d'expiration de **ISSAsynchStatus::WaitForAsynchCompletion** spécifie la durée maximale qui doit s'écouler avant que le contrôle ne soit retourné à l'appelant. Si ce délai expire, DB_S_ASYNCHRONOUS est retourné. L'expiration des délais d'attente n'annule jamais les opérations asynchrones. Si l'application doit annuler une opération asynchrone qui ne se termine pas dans un délai imparti, elle doit attendre l'expiration du délai, puis annuler explicitement l'opération si DB_S_ASYNCHRONOUS est retourné.  
  
> [!NOTE]  
>  Quand les composants du service OLE DB sont utilisés, S_OK peut être retourné quand DB_S_ASYNCHRONOUS est attendu ; ainsi, les applications doivent appeler [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) pour vérifier l’état d’achèvement quand S_OK ou DB_S_ASYNCHRONOUS est retourné.  
  
 Si la valeur de *dwMillisecTimeOut* est INFINITE, la méthode **ISSAsynchStatus::WaitForAsynchCompletion** se bloque jusqu'à ce que l'opération soit terminée. Si la valeur de *dwMillisecTimeOut* est 0, la méthode est retournée immédiatement avec l'état de l'opération en attente. Si le délai d'attente expire avant que l'opération ne soit terminée, DB_S_ASYNCHRONOUS est retourné.  
  
 Si l'opération se termine avant l'expiration du délai d'attente, le HRESULT retourné correspond au HRESULT retourné par l'opération (HRESULT retourné si l'opération était effectuée de façon synchrone).  
  
 De plus, la propriété SSPROP_ISSAsynchStatus a été ajoutée au jeu de propriétés DBPROPSET_SQLSERVERROWSET. Les fournisseurs qui prennent en charge l’interface [ISSAsynchStatus](issasynchstatus-ole-db.md) doivent implémenter cette propriété avec la valeur VARIANT_TRUE.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations asynchrones](../native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](issasynchstatus-ole-db.md)  
  
  
