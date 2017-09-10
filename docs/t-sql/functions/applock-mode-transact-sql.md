---
title: APPLOCK_MODE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APPLOCK_MODE_TSQL
- APPLOCK_MODE
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- APPLOCK_MODE function
ms.assetid: e43d4917-77f1-45cc-b231-68ba7fee3385
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ceec0a5465187e1b470bd9eb8b1039a5b3d60aae
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="applockmode-transact-sql"></a>APPLOCK_MODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Renvoie le mode de verrouillage détenu par le propriétaire du verrou sur une ressource d'application particulière. APPLOCK_MODE est une fonction de verrouillage d'application qui agit sur la base de données active. L'étendue des verrous d'application est la base de données.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
APPLOCK_MODE( 'database_principal' , 'resource_name' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Arguments  
'*principal_base_de_données*'  
Utilisateur, rôle ou rôle d'application qui peut se voir octroyer des autorisations sur des objets dans la base de données. L’appelant de la fonction doit être un membre du *principal_base_de_données*, dbo ou db_owner fixe le rôle de base de données afin d’appeler la fonction.
  
'*nom_ressource*'  
Nom de ressource de verrou spécifié par l'application cliente. L'application doit vérifier que le nom de ressource est unique. Le nom spécifié est haché en interne en une valeur qui peut être stockée dans le gestionnaire de verrous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name*est **nvarchar (255)** sans valeur par défaut. *resource_name* est binaire et respecte la casse, indépendamment des paramètres de classement de la base de données actuelle.
  
'*lock_owner*'  
Est le propriétaire du verrou, qui est la *lock_owner* valeur lorsque le verrou a été demandé. *lock_owner* est **nvarchar(32)**, la valeur peut être **Transaction** (la valeur par défaut) ou **Session**.
  
## <a name="return-types"></a>Types de retour
**nvarchar(32)**
  
## <a name="return-value"></a>Valeur retournée
Renvoie le mode de verrouillage détenu par le propriétaire du verrou sur une ressource d'application particulière. Le mode de verrouillage peut avoir une des valeurs suivantes :
  
||||  
|-|-|-|  
|**NoLock**|**Update**|**\*SharedIntentExclusive**|  
|**IntentShared**|**IntentExclusive**|**\*UpdateIntentExclusive**|  
|**Partagé**|**Exclusive**||  
  
*Ce mode de verrouillage est une combinaison d'autres modes de verrouillage ; il n'est pas possible de l'acquérir explicitement en utilisant sp_getapplock.
  
## <a name="function-properties"></a>Propriétés de la fonction
**Non déterministes**
  
**Non indexable**
  
**Non Parallélisable**
  
## <a name="examples"></a>Exemples  
Deux utilisateurs (A et B) exécutent la suite d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante dans des sessions différentes.
  
L'utilisateur A exécute :
  
```sql
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result=sp_getapplock  
    @DbPrincipal='public',  
    @Resource='Form1',  
    @LockMode='Shared',  
    @LockOwner='Transaction';  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
GO  
```  
  
L'utilisateur B exécute :
  
```sql
Use AdventureWorks2012;  
GO  
BEGIN TRAN;  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
--Result set: NoLock  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Shared', 'Transaction');  
--Result set: 1 (Lock is grantable.)  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: 0 (Lock is not grantable.)  
GO  
```  
  
L'utilisateur A exécute ensuite :
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
L'utilisateur B exécute :
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
Les utilisateurs A et B exécutent ensuite :
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[APPLOCK_TEST &#40; Transact-SQL &#41;](../../t-sql/functions/applock-test-transact-sql.md)  
[sp_getapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  

