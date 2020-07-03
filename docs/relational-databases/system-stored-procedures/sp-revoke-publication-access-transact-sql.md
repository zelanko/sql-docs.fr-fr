---
title: sp_revoke_publication_access (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_revoke_publication_access_TSQL
- sp_revoke_publication_access
helpviewer_keywords:
- sp_revoke_publication_access
ms.assetid: 84ed9e77-991f-4fa5-a21f-7c6bfec1b3e3
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: cb9b695000cbeb359eb6b762c8d1800651aa963f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901370"
---
# <a name="sp_revoke_publication_access-transact-sql"></a>sp_revoke_publication_access (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Supprime la connexion à partir d'une liste d'accès aux publications. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_revoke_publication_access [ @publication = ] 'publication' , [ @login = ] 'login'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication à laquelle accéder. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @login = ] 'login'`ID de connexion. *login* est de **type sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_revoke_publication_access** est utilisé dans les réplications d’instantané, transactionnelles et de fusion.  
  
 **sp_revoke_publication_access** peut être appelée à plusieurs reprises.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_revoke_publication_access**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_grant_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [sp_help_publication_access &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md)   
 [Sécuriser le serveur de publication](../../relational-databases/replication/security/secure-the-publisher.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
