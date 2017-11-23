---
title: "REFUSER des autorisations d’objet système (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- DENY statement, system objects
- encryption [SQL Server], system objects
- system objects [SQL Server]
- cryptography [SQL Server], system objects
ms.assetid: 4e43f954-0982-470b-a239-08a13c61563a
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8d584aa3c7329b8f81e445f612e7041cd14e0747
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deny-system-object-permissions-transact-sql"></a>DENY – refus d'autorisations d'objet système (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Permet de refuser des autorisations sur des objets système tels que des procédures stockées, des procédures stockées étendues, des fonctions et des vues.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DENY { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
## <a name="arguments"></a>Arguments  
 [ **sys.** ]  
 Le **sys** qualificateur est nécessaire uniquement lorsque vous faites référence à des affichages catalogue et vues de gestion dynamique.  
  
 *system_object*  
 Spécifie l'objet sur lequel l'autorisation doit être refusée.  
  
 *principal*  
 Spécifie le principal pour lequel l'autorisation est révoquée.  
  
## <a name="remarks"></a>Notes  
 Cette instruction permet de refuser des autorisations sur des procédures stockées, procédures stockées étendues, fonctions table, fonctions scalaires, vues, affichages catalogue, vues de compatibilité, vues INFORMATION_SCHEMA, vues de gestion dynamique et tables système installées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chacun de ces objets système existe comme un enregistrement unique dans la base de données de ressources (**mssqlsystemresource**). La base de données des ressources est en lecture seule. Un lien vers l’objet est exposé comme un enregistrement dans le **sys** schéma de chaque base de données.  
  
 La résolution de noms par défaut permet de résoudre les noms de procédures non qualifiés dans la base de données des ressources. Par conséquent, le **sys** qualificateur est uniquement requis lorsque vous spécifiez des affichages catalogue et vues de gestion dynamique.  
  
> [!CAUTION]  
>  Le refus d'autorisations sur des objets système entraîne l'échec des applications qui en dépendent. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise les affichages catalogue et peut ne pas fonctionner comme prévu si vous modifiez les autorisations par défaut sur les affichages catalogue.  
  
 Le refus d'autorisations sur des déclencheurs et sur des colonnes d'objets système n'est pas pris en charge.  
  
 Les autorisations sur les objets système sont conservées lors d'une mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les objets système sont consultables dans l’affichage catalogue [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) . Les autorisations sur les objets système sont consultables dans l’affichage catalogue [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) dans la base de données **master** .  
  
 La requête ci-dessous retourne des informations sur les autorisations des objets système :  
  
```  
SELECT * FROM master.sys.database_permissions AS dp   
    JOIN sys.system_objects AS so  
    ON dp.major_id = so.object_id  
    WHERE dp.class = 1 AND so.parent_object_id = 0 ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, l'autorisation `EXECUTE` sur `xp_cmdshell` est refusée à `public`.  
  
```  
DENY EXECUTE ON sys.xp_cmdshell TO public;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)   
 [Sys.database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [ACCORDER des autorisations d’objet système &#40; Transact-SQL &#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [Autorisations d’objet système REVOKE &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)  
  
  
