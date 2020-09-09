---
description: sp_msx_defect (Transact-SQL)
title: sp_msx_defect (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a1b5ea1139e0cfc1b27d7b79df29e6c1b1381b4d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541539"
---
# <a name="sp_msx_defect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Supprime le serveur actuel des opérations multiserveur.  
  
> [!CAUTION]  
>  **sp_msx_defect** modifie le registre. La modification manuelle du Registre n'est pas recommandée parce que des modifications inadaptées ou incorrectes peuvent provoquer de graves problèmes de configuration à votre système. Seuls des utilisateurs expérimentés peuvent utiliser regedit.exe pour modifier le Registre. Pour plus d’informations, consultez la documentation de Microsoft Windows.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>Arguments  
`[ @forced_defection = ] forced_defection` Spécifie s’il faut ou non forcer la désinscription si le serveur SQLServerAgent principal a été définitivement perdu en raison d’une base de données **msdb** irrémédiablement endommagée ou de la sauvegarde d’une base de données **msdb** . *forced_defection*est de **bit**, avec **0**comme valeur par défaut, qui indique qu’aucune désinscription forcée ne doit se produire. La valeur **1** force la désinscription.  
  
 Après avoir forcé une désinscription en exécutant **sp_msx_defect**, un membre du rôle serveur fixe **sysadmin** sur le serveur SQLServerAgent maître doit exécuter la commande suivante pour terminer la désinscription :  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Lorsque **sp_msx_defect** se termine correctement, un message est retourné.  
  
## <a name="permissions"></a>Autorisations  
 Pour exécuter cette procédure stockée, l'utilisateur doit être membre du rôle de serveur fixe **sysadmin** .  
  
## <a name="see-also"></a>Voir aussi  
 [sp_msx_enlist &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
