---
title: ORIGINAL_DB_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ORIGINAL_DB_NAME
- ORIGINAL_DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ORIGINAL_DB_NAME function
ms.assetid: 7dadc40a-1287-4f31-8487-434ee477144d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8782f07e774d48c371a558fa6626ef09e372ab30
ms.sourcegitcommit: 032273bfbc240fe22ac6c1f6601a14a6d99573f7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2019
ms.locfileid: "55513779"
---
# <a name="originaldbname-transact-sql"></a>ORIGINAL_DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le nom de base de données spécifié par l'utilisateur dans la chaîne de connexion de base de données. Cette base de données est spécifié en utilisant l’option **sqlcmd-d** (*base de données* USE). Elle peut également être spécifiée avec l’expression de source de données Open Database Connectivity (ODBC) (catalogue initial =*databasename*).  
  
 Cette base de données est différente de la base de données utilisateur par défaut.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ORIGINAL_DB_NAME ()  
```  
  
## <a name="remarks"></a>Notes   
 Si la base de données initiale n'est pas spécifiée, la fonction retourne une chaîne vide.  
  
## <a name="see-also"></a> Voir aussi  
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Utilitaire osql](../../tools/osql-utility.md)   
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
