---
title: Syntaxe de la commande | Microsoft Docs
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
ms.openlocfilehash: 2d06b72d21dec6e335ef438f0be7838cee4a1231
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304492"
---
# <a name="command-syntax"></a>Syntaxe de la commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB reconnaît la syntaxe de commande spécifiée par la macro DBGUID_SQL. Pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de DB OLE de client autochtone, le spécificateur [!INCLUDE[tsql](../../includes/tsql-md.md)] indique qu’un amalgame de ODBC SQL, ISO, et est une syntaxe valide. Par exemple, l'instruction SQL suivante utilise une séquence d'échappement ODBC SQL pour spécifier la fonction de chaîne LCASE :  
  
```  
SELECT customerid={fn LCASE(CustomerID)} FROM Customers  
```  
  
 LCASE retourne une chaîne de caractères, en convertissant toutes les majuscules en leurs équivalents minuscules. La fonction de chaîne ISO LOWER effectue la même opération, si bien que l'instruction SQL suivante correspond à l'équivalent ISO de l'instruction ODBC présentée ci-dessus :  
  
```  
SELECT customerid=LOWER(CustomerID) FROM Customers  
```  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE du client autochtone traite avec succès l’une ou l’autre forme de la déclaration lorsqu’il est spécifié comme texte pour une commande.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 Lors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’exécution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’une procédure stockée à l’aide d’une commande de fournisseur de DB OLE Native Client, utilisez la séquence d’évacuation ODBC CALL dans le texte de commande. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise ensuite le mécanisme d’appel de procédure à distance pour optimiser le traitement des commandes. Par exemple, l'instruction ODBC SQL suivante correspond à un texte de commande préféré par rapport à la forme [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
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
  
  
