---
title: Utilisation des transactions | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 93d68ba9d289889b2f25c2782bcdbc4266adf2a7
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008643"
---
# <a name="using-transactions"></a>Utilisation de transactions
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Dans SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects), le traitement transactionnel est effectué par le biais de la connexion à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Common.ServerConnection>. L' <xref:Microsoft.SqlServer.Management.Common.ServerConnection> objet est référencé par la <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> propriété de l' <xref:Microsoft.SqlServer.Management.Smo.Server> objet lorsque la connexion est établie. Des méthodes telles que <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> et <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A> appartiennent à la propriété de l'objet <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de programmes SMO](../../../relational-databases/server-management-objects-smo/create-program/creating-smo-programs.md)  
  
  
