---
title: "La file d’attente de suppression (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP QUEUE
- DROP_QUEUE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dropping queues
- queues [Service Broker], removing
- deleting queues
- DROP QUEUE statement
- removing queues
ms.assetid: fd866520-ca00-477d-b2e9-0110e9610ed4
caps.latest.revision: "33"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3be4f36943d6e25bb520a28593d009e7a8373c48
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="drop-queue-transact-sql"></a>DROP QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une file d'attente existante.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP QUEUE <object>  
[ ; ]  
  
<object> ::=  
{  
    [ database_name . [ schema_name ] . | schema_name . ]  
        queue_name  
}  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Nom de la base de données qui contient la file d'attente à supprimer. Lorsqu’aucun *nom_base_de_données* est fourni, les valeurs par défaut pour la base de données actuelle.  
  
 *schema_name (object)*  
 Nom du schéma auquel appartient la file d'attente à supprimer. Lorsqu’aucun *schema_name* est fourni, les valeurs par défaut pour le schéma par défaut pour l’utilisateur actuel.  
  
 *queue_name*  
 Nom de la file d'attente à supprimer.  
  
## <a name="remarks"></a>Notes  
 Il est impossible de supprimer une file d'attente si un service y fait référence.  
  
## <a name="permissions"></a>Autorisations  
 L’autorisation de suppression d’une file d’attente par défaut au propriétaire de la file d’attente, les membres de la **db_ddladmin** ou **db_owner** fixe des rôles de base de données et les membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime le **ExpenseQueue** file d’attente à partir de la base de données actuelle.  
  
```  
DROP QUEUE ExpenseQueue ;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md)   
 [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
