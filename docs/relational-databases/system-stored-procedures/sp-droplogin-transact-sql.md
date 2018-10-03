---
title: sp_droplogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droplogin
- sp_droplogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplogin
ms.assetid: e58684d1-c394-48de-906e-da6ee91100c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 05adcc690b1fdb869f8de4d306e989e74d831cf8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659737"
---
# <a name="spdroplogin-transact-sql"></a>sp_droplogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ceci empêche l'accès à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous ce nom de connexion.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_droplogin [ @loginame = ] 'login'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@loginame =** ] **'***connexion***'**  
 Connexion à supprimer. *connexion* est **sysname**, sans valeur par défaut. *connexion* doit déjà exister dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_droplogin** appelle DROP LOGIN.  
  
 **sp_droplogin** ne peut pas être exécutée dans une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY LOGIN sur le serveur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `DROP LOGIN` pour supprimer la connexion `Victoria` d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette méthode est recommandée.  
  
```  
DROP LOGIN Victoria;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
