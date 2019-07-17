---
title: sp_dropserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropserver_TSQL
- sp_dropserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropserver
ms.assetid: 0fc83e35-0caa-49a3-a4b6-a1890d4f46ef
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 0155b154a1d63343c157bc2eca6e5cbd7c1b8968
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124827"
---
# <a name="spdropserver-transact-sql"></a>sp_dropserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Supprime un serveur dans la liste des serveurs liés et distants connus sur l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien](../../database-engine/configure-windows/media/topic-link.gif "Icône de lien") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
sp_dropserver [ @server = ] 'server'   
     [ , [ @droplogins = ] { 'droplogins' | NULL} ]  
```  
  
## <a name="arguments"></a>Arguments  
 *server*  
 Serveur à supprimer. *server* est de type **sysname**et n'a pas de valeur par défaut. *serveur* doit exister.  
  
 *droplogins*  
 Indique qui de connexion de serveur lié et distant pour liés *server* doit également être supprimé si **droplogins** est spécifié. **`@droplogins`** est **char (10)** , avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Si vous exécutez **sp_dropserver** sur un serveur qui est associé à des entrées de connexion de serveur lié et distant, ou est configuré comme serveur de publication de réplication, un message d’erreur est retourné. Pour supprimer toutes les connexions de serveur lié et distant d’un serveur lorsque vous supprimez le serveur, utilisez le **droplogins** argument.  
  
 **sp_dropserver** ne peut pas être exécutée à l’intérieur d’une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite une autorisation ALTER ANY LINKED SERVER sur le serveur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le serveur distant `ACCOUNTS` et toutes les connexions d'accès distant qui lui sont associées dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
sp_dropserver 'ACCOUNTS', 'droplogins';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
