---
title: sp_unsetapprole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_unsetapprole_TSQL
- sp_unsetapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unsetapprole
ms.assetid: 4c4033d3-1a34-4dfb-835d-e3293d1a442d
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f57eb690c679218d9bd8f639e3f3215652351f5b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026938"
---
# <a name="spunsetapprole-transact-sql"></a>sp_unsetapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Désactive un rôle d'application et revient au contexte de sécurité antérieur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_unsetapprole @cookie   
```  
  
## <a name="arguments"></a>Arguments  
 **@cookie**  
 Spécifie le cookie créé lors de l'activation du rôle d'application. Le cookie est créé par [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md). **varbinary (8000)**.  
  
> [!NOTE]  
>  Le paramètre **OUTPUT** de cookie pour **sp_setapprole** est actuellement documenté comme **varbinary(8000)** , ce qui correspond à la longueur maximale correcte. Cependant, l’implémentation actuelle retourne **varbinary(50)**. Les applications doivent continuer à réserver **varbinary (8000)** afin que l’application continue à fonctionner correctement si le cookie de taille de retour augmente dans une version ultérieure.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) et 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Après une application le rôle est activé à l’aide de **sp_setapprole**, le rôle reste actif jusqu'à ce que l’utilisateur se déconnecte du serveur ou exécute **sp_unsetapprole**.  
  
 Pour une vue d’ensemble des rôles d’application, consultez [rôles d’Application](../../relational-databases/security/authentication-access/application-roles.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance au **public** et la connaissance du cookie enregistré lorsque le rôle d’application a été activé.  
  
## <a name="examples"></a>Exemples  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>A. Activation d'un rôle d'application avec un cookie, puis retour au contexte antérieur  
 Dans l'exemple ci-dessous, le rôle d'application `Sales11` est activé avec le mot de passe `fdsd896#gfdbfdkjgh700mM` et un cookie est créé. L’exemple retourne le nom de l’utilisateur actuel, puis revient au contexte d’origine en exécutant **sp_unsetapprole**.  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)  
  
  
