---
description: HOST_ID (Transact-SQL)
title: HOST_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HOST_ID
- HOST_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], workstations
- HOST_ID function
- workstation IDs [SQL Server]
- identification numbers [SQL Server], workstations
ms.assetid: 36ba56d4-20d7-4cd1-aa2a-e40a6c0a4e39
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 099026a22a03c563b8ea176d5fed14d7d936ffc6
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116345"
---
# <a name="host_id-transact-sql"></a>HOST_ID (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne le numéro d'identification de la station de travail. Le numéro d'identification de la station de travail est l'ID de processus (PID) de l'application sur l'ordinateur client qui se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
HOST_ID ()  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 **char(10)**  
  
## <a name="remarks"></a>Remarques  
 Quand le paramètre d'une fonction système est facultatif, la base de données active, l'ordinateur hôte, l'utilisateur du serveur ou l'utilisateur de la base de données sont pris implicitement en considération. Les fonctions intégrées doivent toujours être suivies de parenthèses.  
  
 Les fonctions système peuvent être utilisées dans la liste de sélection, dans une clause WHERE, et partout où une expression est autorisée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une table qui utilise `HOST_ID()` dans une définition `DEFAULT` pour enregistrer l'ID de terminal des ordinateurs qui insèrent des lignes dans une table enregistrant les commandes.  
  
```sql  
CREATE TABLE Orders  
   (OrderID     INT       PRIMARY KEY,  
    CustomerID  NCHAR(5)  REFERENCES Customers(CustomerID),  
    TerminalID  CHAR(8)   NOT NULL DEFAULT HOST_ID(),  
    OrderDate   DATETIME  NOT NULL,  
    ShipDate    DATETIME  NULL,  
    ShipperID   INT       NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
