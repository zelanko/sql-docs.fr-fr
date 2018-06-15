---
title: Exécution d’une commande | Documents Microsoft
description: Exécution d’une commande
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 20d2a7314db4a70fbc27221fba34e510441d9236
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665529"
---
# <a name="executing-a-command"></a>Exécution d'une commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Une fois la connexion à une source de données est établie, le consommateur appelle la **IDBCreateSession::CreateSession** méthode pour créer une session. La session agit en guise de commande, d'ensemble de lignes ou de fabrique de transactions.  
  
 Pour travailler directement avec les tables individuelles ou d’index, le consommateur demande le **IOpenRowset** interface. Le **IOpenRowset::OpenRowset** méthode ouvre et retourne un ensemble de lignes qui inclut toutes les lignes à partir d’une seule table de base ou un index.  
  
 Pour exécuter une commande (par exemple, SELECT \* FROM Authors), le consommateur demande le **IDBCreateCommand** interface. Le consommateur peut exécuter le **IDBCreateCommand::CreateCommand** pour créer un objet de commande et de demande pour le **ICommandText** interface. Le **ICommandText::SetCommandText** méthode est utilisée pour spécifier la commande qui doit être exécutée.  
  
 Le **Execute** commande est utilisée pour exécuter la commande. La commande peut être un nom de procédure ou une instruction SQL. Toutes les commandes ne génèrent pas un objet de jeu de résultats (ensemble de lignes). Les commandes, telles que SELECT * FROM Authors, produisent un jeu de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application OLE DB Driver pour SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
