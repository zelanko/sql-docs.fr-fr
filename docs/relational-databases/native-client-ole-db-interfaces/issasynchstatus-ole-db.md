---
description: ISSAsynchStatus (fournisseur Native Client OLE DB)
title: ISSAsynchStatus (fournisseur Native Client OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 340360c49d55d62e38c908e914cd81e7fab6d766
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490822"
---
# <a name="issasynchstatus-native-client-ole-db-provider"></a>ISSAsynchStatus (fournisseur Native Client OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **ISSAsynchStatus** expose la prise en charge des opérations asynchrones [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il s'agit d'une interface facultative qui hérite de l'interface OLE DB de base **IDBAsynchStatus**. Outre les méthodes **Abort** et **GetStatus** héritées de **IDBAsynchStatus**, **ISSAsynchStatus** fournit une nouvelle méthode qui permet d'attendre qu'une opération asynchrone se termine ou qu'un délai d'expiration soit dépassé.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ISSAsynchStatus::Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)|Annule une opération s'exécutant de manière asynchrone.|  
|[ISSAsynchStatus::GetStatus &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)|Retourne l'état d'une opération s'exécutant de manière asynchrone.|  
|[ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)|Attend que l'opération s'exécutant de façon asynchrone se termine ou qu'un délai d'expiration soit dépassé.|  
  
## <a name="remarks"></a>Notes  
 L'implémentation **ISSAsynchStatus** de la méthode **ISSAsynchStatus::GetStatus** est identique à la méthode **IDBAsynchStatus::GetStatus** , à la différence près que si l'initialisation d'un objet source de données est abandonnée, E_UNEXPECTED est retourné au lieu de DB_E_CANCELED (bien que **ISSAsynchStatus::WaitForAsynchCompletion** retourne DB_E_CANCELED). Cela est dû au fait que l'objet source de données ne reste pas dans l'état habituel après une opération d'abandon, afin que d'autres tentatives d'initialisation puissent avoir lieu.  
  
 Les méthodes suivantes prennent en charge l'utilisation d'une exécution asynchrone dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   **ICommand::Execute**  
  
-   **IOpenRowset::OpenRowset**  
  
-   **IMultipleResults::GetResult**  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](https://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Exécution d’opérations asynchrones](../../relational-databases/native-client/features/performing-asynchronous-operations.md)  
  
  
