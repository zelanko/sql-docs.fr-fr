---
title: sp_msx_defect (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
caps.latest.revision: "24"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a9d60318c9e737dd01d80d6ab00b089d98a1fb0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="spmsxdefect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime le serveur actuel des opérations multiserveur.  
  
> [!CAUTION]  
>  **sp_msx_defect** modifie le Registre. La modification manuelle du Registre n'est pas recommandée parce que des modifications inadaptées ou incorrectes peuvent provoquer de graves problèmes de configuration à votre système. Seuls des utilisateurs expérimentés peuvent utiliser regedit.exe pour modifier le Registre. Pour plus d’informations, consultez la documentation de Microsoft Windows.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@forced_defection =**] *défection_forcée*  
 Spécifie s’il faut ou non forcer la désinscription lorsque le SQLServerAgent principal a été définitivement perdu en raison d’une détérioration **msdb** base de données, ou sur non **msdb** sauvegarde de base de données. *défection_forcée*est **bits**, avec une valeur par défaut **0**, ce qui signifie qu’aucune forcer la désinscription. La valeur **1** force la désinscription.  
  
 Après avoir forcé une désinscription par l’exécution de **sp_msx_defect**, un membre de la **sysadmin** rôle serveur fixe auprès du SQLServerAgent principal doit exécuter la commande suivante pour terminer l’opération :  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="remarks"></a>Notes  
 Lorsque **sp_msx_defect** se termine correctement, un message est retourné.  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter cette procédure stockée, l'utilisateur doit être membre du rôle de serveur fixe **sysadmin** .  
  
## <a name="see-also"></a>Voir aussi  
 [sp_msx_enlist &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
