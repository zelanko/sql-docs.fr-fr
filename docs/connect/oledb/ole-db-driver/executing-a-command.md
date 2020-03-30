---
title: Exécution d’une commande | Microsoft Docs
description: Exécution d’une commande
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f13c9177a74212b849572881f114e503a9530286
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67994989"
---
# <a name="executing-a-command"></a>Exécution d'une commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Une fois la connexion à une source de données établie, le consommateur appelle la méthode **IDBCreateSession::CreateSession** pour créer une session. La session agit en guise de commande, d'ensemble de lignes ou de fabrique de transactions.  
  
 Pour utiliser directement des tables individuelles ou des index, le consommateur demande l’interface **IOpenRowset**. La méthode **IOpenRowset::OpenRowset** ouvre et retourne un ensemble de lignes qui inclut toutes les lignes d’une même table de base ou d’un même index.  
  
 Pour exécuter une commande (par exemple SELECT \* FROM Authors), le consommateur demande l’interface **IDBCreateCommand**. Le consommateur peut exécuter la méthode **IDBCreateCommand::CreateCommand** pour créer un objet de commande et demander l'interface **ICommandText**. La méthode **ICommandText::SetCommandText** est utilisée pour spécifier la commande à exécuter.  
  
 La commande **Execute** est utilisée pour exécuter la commande. La commande peut être un nom de procédure ou une instruction SQL. Toutes les commandes ne génèrent pas un objet de jeu de résultats (ensemble de lignes). Les commandes, telles que SELECT * FROM Authors, produisent un jeu de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application OLE DB Driver pour SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
