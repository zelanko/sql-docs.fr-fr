---
title: sp_droplinkedsrvlogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droplinkedsrvlogin_TSQL
- sp_droplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplinkedsrvlogin
ms.assetid: 75a4a040-72d5-4d29-8304-de0aa481ad4b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6d5d2dbded8a1dff8a0445dbafd64b017640357f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843177"
---
# <a name="spdroplinkedsrvlogin-transact-sql"></a>sp_droplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un mappage existant entre une connexion du serveur local exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et une connexion sur le serveur lié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_droplinkedsrvlogin [ @rmtsrvname= ] 'rmtsrvname' ,   
   [ @locallogin= ] 'locallogin'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@rmtsrvname =** ] **'***nom_du_serveur_distant***'**  
 Est le nom d’un serveur lié qui le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’applique le mappage de connexion. *nom_du_serveur_distant* est **sysname**, sans valeur par défaut. *nom_du_serveur_distant* doit déjà exister.  
  
 [  **@locallogin =** ] **'***locallogin***'**  
 Est le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion sur le serveur local qui possède un mappage au serveur lié *nom_du_serveur_distant*. *LocalLogin* est **sysname**, sans valeur par défaut. Un mappage pour *locallogin* à *nom_du_serveur_distant* doit déjà exister. Si NULL, le mappage par défaut créé par **sp_addlinkedserver**, qui mappe toutes les connexions sur le serveur local aux connexions sur le serveur lié, est supprimé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 Lorsque le mappage existant pour une connexion est supprimé, le serveur local utilise le mappage par défaut créé par **sp_addlinkedserver** quand il se connecte au serveur lié pour le compte de cette connexion. Pour modifier le mappage par défaut, utilisez **sp_addlinkedsrvlogin**.  
  
 Si le mappage par défaut est également supprimé, seules les connexions qui ont explicitement reçues un mappage de connexion au serveur lié, à l’aide de **sp_addlinkedsrvlogin**, peut accéder au serveur lié.  
  
 **sp_droplinkedsrvlogin** ne peut pas être exécutée à partir d’une transaction définie par l’utilisateur.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY LOGIN sur le serveur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-removing-the-login-mapping-for-an-existing-user"></a>A. Suppression du mappage de connexion d'un utilisateur existant  
 L'exemple suivant supprime le mappage pour la connexion `Mary` du serveur local vers le serveur lié `Accounts`. Par conséquent, la connexion `Mary` utilise le mappage de connexion par défaut.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', 'Mary';  
```  
  
### <a name="b-removing-the-default-login-mapping"></a>B. Suppression du mappage de connexion par défaut  
 L'exemple suivant supprime le mappage de connexion par défaut créé à l'origine par l'exécution de `sp_addlinkedserver` sur le serveur lié `Accounts`.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', NULL;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
