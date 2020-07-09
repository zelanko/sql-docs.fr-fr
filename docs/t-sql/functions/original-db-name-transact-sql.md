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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 889cdb18a323e64cf1b94bcde57eaf77c37e89d4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892554"
---
# <a name="original_db_name-transact-sql"></a>ORIGINAL_DB_NAME (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne le nom de base de données spécifié par l'utilisateur dans la chaîne de connexion de base de données. Cette base de données est spécifié en utilisant l’option **sqlcmd-d** (*base de données* USE). Elle peut également être spécifiée avec l’expression de source de données Open Database Connectivity (ODBC) (catalogue initial =*databasename*).  
  
 Cette base de données est différente de la base de données utilisateur par défaut.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ORIGINAL_DB_NAME ()  
```  
  
## <a name="remarks"></a>Notes  
 Si la base de données initiale n'est pas spécifiée, la fonction retourne une chaîne vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire sqlcmd](../../tools/sqlcmd-utility.md)   
 [Utilitaire osql](../../tools/osql-utility.md)   
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
