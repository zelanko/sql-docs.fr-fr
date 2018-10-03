---
title: À l’aide de Transactions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7d00f22d8e7cf8b01e35dc12482c8fe7dcfcde9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47693927"
---
# <a name="using-transactions"></a>Utilisation de transactions
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Dans SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects), le traitement transactionnel est effectué par le biais de la connexion à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. Le <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet est référencé par le <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété de la <xref:Microsoft.SqlServer.Management.Smo.Server> de l’objet lorsque la connexion est établie. Des méthodes telles que <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> et <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> appartiennent à la propriété de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de programmes SMO](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
