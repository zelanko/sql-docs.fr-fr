---
description: DROP MESSAGE TYPE (Transact-SQL)
title: DROP MESSAGE TYPE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_MESSAGE_TYPE_TSQL
- DROP MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- message types [Service Broker], removing
- deleting message types
- dropping message types
- DROP MESSAGE TYPE statement
- removing message types
ms.assetid: 805e8ad5-8a93-49f0-88e5-e6fca8814dd5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b93b022ed1937b3923a44d5c13b62ff2038df958
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478824"
---
# <a name="drop-message-type-transact-sql"></a>DROP MESSAGE TYPE (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Supprime un type de message existant.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
  
DROP MESSAGE TYPE message_type_name  
[ ; ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *message_type_name*  
 Nom du type de message à supprimer. Les noms du serveur, de la base de données et du schéma ne peuvent pas être spécifiés.  
  
## <a name="permissions"></a>Autorisations  
 L'autorisation de suppression d'un type de message revient par défaut au propriétaire du type de message, aux membres des rôles de base de données fixes db_ddladmin et db_owner et aux membres du rôle serveur fixe sysadmin.  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez pas supprimer un type de message si un contrat y fait référence.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le type de message `//Adventure-Works.com/Expenses/SubmitExpense` de la base de données.  
  
```  
DROP MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense] ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
