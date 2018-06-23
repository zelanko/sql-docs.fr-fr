---
title: ISSAsynchStatus (OLE DB) | Documents Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a67b1efda62d76bd947dcbc9291f47be7f5f907d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039742"
---
# <a name="issasynchstatus-ole-db"></a>ISSAsynchStatus (OLE DB)
  **ISSAsynchStatus** expose la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des opérations asynchrones. Il s'agit d'une interface facultative qui hérite de l'interface OLE DB de base **IDBAsynchStatus**. Outre les méthodes **Abort** et **GetStatus** héritées de **IDBAsynchStatus**, **ISSAsynchStatus** fournit une nouvelle méthode qui permet d'attendre qu'une opération asynchrone se termine ou qu'un délai d'expiration soit dépassé.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort &#40;OLE DB&#41;](issasynchstatus-abort-ole-db.md)|Annule une opération s'exécutant de manière asynchrone.|  
|[ISSAsynchStatus::GetStatus &#40;OLE DB&#41;](issasynchstatus-getstatus-ole-db.md)|Retourne l'état d'une opération s'exécutant de manière asynchrone.|  
|[ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;](issasynchstatus-waitforasynchcompletion-ole-db.md)|Attend que l'opération s'exécutant de façon asynchrone se termine ou qu'un délai d'expiration soit dépassé.|  
  
## <a name="remarks"></a>Notes  
 L'implémentation **ISSAsynchStatus** de la méthode **ISSAsynchStatus::GetStatus** est identique à la méthode **IDBAsynchStatus::GetStatus** , à la différence près que si l'initialisation d'un objet source de données est abandonnée, E_UNEXPECTED est retourné au lieu de DB_E_CANCELED (bien que **ISSAsynchStatus::WaitForAsynchCompletion** retourne DB_E_CANCELED). Cela est dû au fait que l'objet source de données ne reste pas dans l'état habituel après une opération d'abandon, afin que d'autres tentatives d'initialisation puissent avoir lieu.  
  
 Les méthodes suivantes prennent en charge l'utilisation d'une exécution asynchrone dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [Exécution d’opérations asynchrones](../native-client/features/performing-asynchronous-operations.md)  
  
  