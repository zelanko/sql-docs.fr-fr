---
title: ALTER MESSAGE TYPE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_MESSAGE_TYPE_TSQL
- ALTER MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER MESSAGE TYPE statement
- modifying message types
- message types [Service Broker], modifying
ms.assetid: 98c94176-2bdf-4725-b4bc-d33b6b14817d
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0aff23be0cf324678cbe565c0f0c7a3c92d13a3e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="alter-message-type-transact-sql"></a>ALTER MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d'un type de message.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER MESSAGE TYPE message_type_name  
   VALIDATION =  
    {  NONE   
     | EMPTY   
     | WELL_FORMED_XML   
     | VALID_XML WITH SCHEMA COLLECTION schema_collection_name }  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *message_type_name*  
 Nom du type de message à modifier. Les noms du serveur, de la base de données et du schéma ne peuvent pas être spécifiés.  
  
 VALIDATION  
 Spécifie comment [!INCLUDE[ssSB](../../includes/sssb-md.md)] valide le corps des messages de ce type.  
  
 Aucune  
 Aucune validation n'est effectuée. Le corps du message peut contenir tout type de données ou avoir la valeur NULL.  
  
 EMPTY  
 Le corps du message doit être NULL.  
  
 WELL_FORMED_XML  
 Le corps du message doit contenir un document XML bien formé.  
  
 VALID_XML_WITH_SCHEMA = *schema_collection_name*  
 Le corps du message doit contenir du code XML conforme à un schéma de la collection de schémas spécifiée. Le *schema_collection_name* doit être le nom d’une collection de schémas XML existante.  
  
## <a name="remarks"></a>Notes  
 Modifier la validation d'un type de message n'a aucun impact sur les messages qui ont déjà été remis à une file d'attente.  
  
 L'instruction ALTER AUTHORIZATION permet de modifier l'AUTORISATION pour un type de message.  
  
## <a name="permissions"></a>Autorisations  
 L’autorisation de modification d’un type de message par défaut est le propriétaire du type de message, les membres de la **db_ddladmin** ou **db_owner** fixe des rôles de base de données et les membres de la **sysadmin** rôle serveur fixe.  
  
 Si l'instruction ALTER MESSAGE TYPE indique une collections de schémas, l'utilisateur qui exécute cette instruction doit disposer de l'autorisation REFERENCES sur la collection de schémas spécifiée.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique comment changer le type de message `//Adventure-Works.com/Expenses/SubmitExpense` pour demander que le corps du message contienne un document XML correctement formé.  
  
```  
ALTER MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]  
    VALIDATION = WELL_FORMED_XML ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-message-type-transact-sql.md)   
 [DROP MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
