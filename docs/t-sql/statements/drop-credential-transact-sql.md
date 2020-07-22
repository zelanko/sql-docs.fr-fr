---
title: DROP CREDENTIAL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP CREDENTIAL
- DROP_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing credentials
- DROP CREDENTIAL statement
- credentials [SQL Server], DROP CREDENTIAL statement
- authentication [SQL Server], credentials
- deleting credentials
- dropping credentials
ms.assetid: df22c826-317d-45a6-b078-186acb65f71e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c86550e6854cbfcb547a8734f05e910e25df2b5a
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86485495"
---
# <a name="drop-credential-transact-sql"></a>DROP CREDENTIAL (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Permet de supprimer des informations d'identification du serveur.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP CREDENTIAL credential_name  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *credential_name*  
 Nom des informations d'identification à supprimer du serveur.  
  
## <a name="remarks"></a>Notes  
 Pour supprimer le secret associé aux informations d’identification sans supprimer les informations d’identification elles-mêmes, utilisez [ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md).  
  
 Des informations sur les informations d’identification sont consultables dans la vue de catalogue **sys.credentials**.  
  
> [!WARNING]  
>  Les proxies sont associés à des informations d'identification. La suppression d'informations d'identification utilisées par un proxy rend le proxy associé inutilisable. Quand vous supprimez des informations d’identification utilisées par un proxy, supprimez le proxy (à l’aide de [sp_delete_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)) et recréez le proxy associé à l’aide de [sp_add_proxy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation ALTER ANY CREDENTIAL. Pour la suppression d'informations d'identification système, l'autorisation CONTROL SERVER est requise.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous, des informations d'identification nommées `Saddles` sont supprimées.  
  
```  
DROP CREDENTIAL Saddles;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [ALTER CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
