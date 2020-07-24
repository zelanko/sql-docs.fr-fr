---
title: Syntaxe de commande (Native Client OLE DB Provider) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, commands
- commands [OLE DB]
- SQL Server Native Client OLE DB provider, stored procedures
- stored procedures [OLE DB], command syntax
ms.assetid: d463d3d7-e5cb-426d-8e92-aa29980356b6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b927ef211c21773eeccd183a4f18bab8ae5e6e91
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942886"
---
# <a name="command-syntax"></a>Syntaxe de la commande
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client reconnaît la syntaxe de commande spécifiée par la macro DBGUID_SQL. Pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client, le spécificateur indique qu’un amalgame de ODBC SQL, ISO et [!INCLUDE[tsql](../../includes/tsql-md.md)] est une syntaxe valide. Par exemple, l'instruction SQL suivante utilise une séquence d'échappement ODBC SQL pour spécifier la fonction de chaîne LCASE :  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE retourne une chaîne de caractères, en convertissant toutes les majuscules en leurs équivalents minuscules. La fonction de chaîne ISO LOWER effectue la même opération, si bien que l'instruction SQL suivante correspond à l'équivalent ISO de l'instruction ODBC présentée ci-dessus :  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client traite les deux formes de l’instruction avec succès lorsqu’il est spécifié sous forme de texte pour une commande.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 Lors de l’exécution d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] procédure stockée à l’aide d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commande du fournisseur OLE DB Native Client, utilisez la séquence d’échappement ODBC Call dans le texte de la commande. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client utilise ensuite le mécanisme d’appel de procédure distante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour optimiser le traitement des commandes. Par exemple, l'instruction ODBC SQL suivante correspond à un texte de commande préféré par rapport à la forme [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
-   ODBC SQL  
  
    ```  
    {call SalesByCategory('Produce', '1995')}  
    ```  
  
-   Transact-SQL  
  
    ```  
    EXECUTE SalesByCategory 'Produce', '1995'  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
