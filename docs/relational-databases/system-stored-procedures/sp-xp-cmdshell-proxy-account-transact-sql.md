---
title: sp_xp_cmdshell_proxy_account (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6f465a27aeac13a8c0a0e810d52aacccc6022133
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722971"
---
# <a name="sp_xp_cmdshell_proxy_account-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Crée des informations d’identification de proxy pour **xp_cmdshell**.  
  
> [!NOTE]  
>  **xp_cmdshell** est désactivé par défaut. Pour activer **xp_cmdshell**, consultez [Xp_cmdshell option de configuration de serveur](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>Arguments  
 NULL  
 Indique que les informations d'identification de proxy doivent être supprimées.  
  
 *account_name*  
 Spécifie la connexion Windows qui doit être le proxy.  
  
 *mot de passe*  
 Spécifie le mot de passe du compte Windows.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Les informations d’identification du proxy sont appelées **# #xp_cmdshell_proxy_account # #**.  
  
 Lorsqu’il est exécuté à l’aide de l’option NULL, **sp_xp_cmdshell_proxy_account** supprime les informations d’identification du proxy.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-the-proxy-credential"></a>R. Création d'informations d'identification de proxy  
 L'exemple ci-dessous montre comment créer des informations d'identification de proxy pour un compte Windows nommé `ADVWKS\Max04` avec le mot de passe `ds35efg##65`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>B. Suppression des informations d'identification de proxy  
 Dans l'exemple ci-dessous, les informations d'identification de proxy sont supprimées de la banque d'informations d'identification.  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [xp_cmdshell &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [CRÉER des informations d’identification &#40;&#41;Transact-SQL](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys. Credential &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
