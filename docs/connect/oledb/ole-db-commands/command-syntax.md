---
title: Syntaxe de commande | Microsoft Docs
description: Syntaxe de commande et procédures stockées
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- commands [OLE DB]
- OLE DB Driver for SQL Server, stored procedures
- stored procedures [OLE DB], command syntax
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 15d6d221c9e3435a3ba4c3f58c7d6b6e55314f29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016122"
---
# <a name="command-syntax"></a>Syntaxe de la commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server reconnaît la syntaxe de commande spécifiée par la macro DBGUID_SQL. Pour le pilote OLE DB pour SQL Server, le spécificateur indique qu’un amalgame de ODBC SQL, ISO et [!INCLUDE[tsql](../../../includes/tsql-md.md)] est une syntaxe valide. Par exemple, l'instruction SQL suivante utilise une séquence d'échappement ODBC SQL pour spécifier la fonction de chaîne LCASE :  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE retourne une chaîne de caractères, en convertissant toutes les majuscules en leurs équivalents minuscules. La fonction de chaîne ISO LOWER effectue la même opération, si bien que l'instruction SQL suivante correspond à l'équivalent ISO de l'instruction ODBC présentée ci-dessus :  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Le pilote OLE DB pour SQL Server traite correctement chaque forme de l’instruction quand elle est spécifiée en tant que texte pour une commande.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 Quand vous exécutez une procédure stockée [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en utilisant une commande du pilote OLE DB pour SQL Server, utilisez la séquence d’échappement ODBC CALL dans le texte de la commande. Le pilote OLE DB pour SQL Server utilise alors le mécanisme d’appel de procédure distante de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour optimiser le traitement des commandes. Par exemple, l'instruction ODBC SQL suivante correspond à un texte de commande préféré par rapport à la forme [!INCLUDE[tsql](../../../includes/tsql-md.md)] :  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../oledb/ole-db-commands/commands.md)  
  
  
