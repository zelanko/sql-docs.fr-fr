---
title: sp_helplinkedsrvlogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helplinkedsrvlogin_TSQL
- sp_helplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplinkedsrvlogin
ms.assetid: a2b1eba0-bf71-47e7-a4c7-9f55feec82a3
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74f2885b8b1226afbcd7f4aceb4d6f5835e20a0b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036571"
---
# <a name="sphelplinkedsrvlogin-transact-sql"></a>sp_helplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations sur le mappage des connexions défini sur un serveur lié spécifique utilisé pour les requêtes distribuées et les procédures stockées distantes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helplinkedsrvlogin [ [ @rmtsrvname = ] 'rmtsrvname' ]   
     [ , [ @locallogin = ] 'locallogin' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@rmtsrvname=**] **'***nom_du_serveur_distant***'**  
 Nom du serveur lié auquel s'applique le mappage de connexion. *nom_du_serveur_distant* est **sysname**, avec NULL comme valeur par défaut. Si cet argument a la valeur NULL, tous les mappages de connexions précisés sur les serveurs liés définis sur l'ordinateur local exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont renvoyés.  
  
 [  **@locallogin=**] **'***locallogin***'**  
 Est le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion sur le serveur local qui possède un mappage au serveur lié *nom_du_serveur_distant*. *LocalLogin* est **sysname**, avec NULL comme valeur par défaut. NULL indique que tous les mappages de connexion définis sur *nom_du_serveur_distant* sont retournés. Si ce n’est pas NULL, un mappage pour *locallogin* à *nom_du_serveur_distant* doit déjà exister. *LocalLogin* peut être un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou un utilisateur Windows. L'utilisateur Windows doit avoir une autorisation d'accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] directe ou par son appartenance à un groupe Windows qui possède une autorisation d'accès.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Serveur lié**|**sysname**|Nom du serveur lié.|  
|**Connexion locale**|**sysname**|Connexion locale à laquelle s'applique le mappage.|  
|**Est le mappage automatique**|**smallint**|0 = **connexion locale** est mappé à **Remote Login** lors de la connexion à **serveur lié**.<br /><br /> 1 = **connexion locale** est mappé à la même connexion et mot de passe lors de la connexion à **serveur lié**.|  
|**Connexion à distance**|**sysname**|Nom de connexion sur **LinkedServer** qui est mappé à **LocalLogin** lorsque **IsSelfMapping** est 0. Si **IsSelfMapping** est 1, **RemoteLogin** a la valeur NULL.|  
  
## <a name="remarks"></a>Notes  
 Avant de supprimer des mappages de connexion, utilisez **sp_helplinkedsrvlogin** pour déterminer les serveurs liés qui sont impliqués.  
  
## <a name="permissions"></a>Permissions  
 Sans les autorisations sont vérifiées.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-displaying-all-login-mappings-for-all-linked-servers"></a>A. Affichage de tous les mappages de connexion des serveurs liés  
 Le code exemple suivant affiche tous les mappages de connexion de tous les serveurs liés définis sur l'ordinateur local qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helplinkedsrvlogin;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Accounts         NULL          1               NULL  
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
Marketing        NULL          1               NULL  
  
(4 row(s) affected)  
```  
  
### <a name="b-displaying-all-login-mappings-for-a-linked-server"></a>B. Affichage de tous les mappages de connexion d'un serveur lié  
 Le code exemple suivant affiche tous les mappages de connexion définis localement pour le serveur lié `Sales`.  
  
```  
EXEC sp_helplinkedsrvlogin 'Sales';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
### <a name="c-displaying-all-login-mappings-for-a-local-login"></a>C. Affichage de tous les mappages de connexion d'une connexion locale  
 Le code exemple suivant affiche tous les mappages de connexion définis localement pour la connexion `Mary`.  
  
```  
EXEC sp_helplinkedsrvlogin NULL, 'Mary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
