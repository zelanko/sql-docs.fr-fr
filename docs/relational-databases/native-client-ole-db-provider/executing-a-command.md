---
title: Exécution d’une commande | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 266cf6733c2a73f64dc6561e0cb0b13c6929a8b8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423948"
---
# <a name="executing-a-command"></a>Exécution d'une commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Une fois la connexion à une source de données est établie, le consommateur appelle la **IDBCreateSession::CreateSession** méthode pour créer une session. La session agit en guise de commande, d'ensemble de lignes ou de fabrique de transactions.  
  
 Pour travailler directement avec des tables individuelles ou des index, le consommateur demande le **IOpenRowset** interface. Le **IOpenRowset::OpenRowset** méthode ouvre et retourne un ensemble de lignes qui inclut toutes les lignes à partir d’une seule table de base ou un index.  
  
 Pour exécuter une commande (par exemple, SELECT \* FROM Authors), le consommateur demande le **IDBCreateCommand** interface. Le consommateur peut exécuter le **IDBCreateCommand::CreateCommand** méthode pour créer un objet de commande et de demande pour le **ICommandText** interface. Le **ICommandText::SetCommandText** méthode est utilisée pour spécifier la commande qui doit être exécuté.  
  
 Le **Execute** commande est utilisée pour exécuter la commande. La commande peut être un nom de procédure ou une instruction SQL. Toutes les commandes ne génèrent pas un objet de jeu de résultats (ensemble de lignes). Les commandes, telles que SELECT * FROM Authors, produisent un jeu de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application de fournisseur OLE DB de SQL Server Native Client](../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
