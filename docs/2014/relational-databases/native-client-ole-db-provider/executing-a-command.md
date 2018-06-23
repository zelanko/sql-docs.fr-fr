---
title: Exécution d’une commande | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [SQL Server Native Client]
- OLE DB, executing commands
- sessions [SQL Server Native Client]
- OLE DB extensions for XML
- SQL Server Native Client OLE DB provider, command execution
ms.assetid: bb0b3cbf-fe45-46ba-b2ec-c5a39e3c7081
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2d9c0f935bf4d3cd903346281080a8b08384c1e4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140500"
---
# <a name="executing-a-command"></a>Exécution d'une commande
  Une fois la connexion à une source de données est établie, le consommateur appelle la **IDBCreateSession::CreateSession** méthode pour créer une session. La session agit en guise de commande, d'ensemble de lignes ou de fabrique de transactions.  
  
 Pour utiliser directement des tables individuelles ou des index, le consommateur demande l'interface `IOpenRowset`. La méthode `IOpenRowset::OpenRowset` ouvre et retourne un ensemble de lignes qui inclut toutes les lignes d'une table de base ou d'un index unique.  
  
 Pour exécuter une commande (par exemple, SELECT \* FROM Authors), le consommateur demande le `IDBCreateCommand` interface. Le consommateur peut exécuter la méthode `IDBCreateCommand::CreateCommand` pour créer un objet de commande et demander l'interface `ICommandText`. La méthode `ICommandText::SetCommandText` est utilisée pour spécifier la commande à exécuter.  
  
 La commande `Execute` permet d'exécuter la commande. La commande peut être un nom de procédure ou une instruction SQL. Toutes les commandes ne génèrent pas un objet de jeu de résultats (ensemble de lignes). Les commandes, telles que SELECT * FROM Authors, produisent un jeu de résultats.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application de fournisseur OLE DB de SQL Server Native Client](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  