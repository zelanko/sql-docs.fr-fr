---
description: sp_addextendedproc (Transact-SQL)
title: sp_addextendedproc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a64b9b173b6b76429723c47bcf55fab4257b073c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447402"
---
# <a name="sp_addextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enregistre le nom d’une nouvelle procédure stockée étendue dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt l' [intégration du CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @functname = ] 'procedure'` Nom de la fonction à appeler dans la bibliothèque de liens dynamiques (DLL). la *procédure* est **nvarchar (517)**, sans valeur par défaut. la *procédure* peut éventuellement inclure le nom du propriétaire sous la forme *propriétaire. Function*.  
  
`[ @dllname = ] 'dll'` Nom de la DLL qui contient la fonction. *dll* est de type **varchar (255)**, sans valeur par défaut. Il est recommandé de spécifier le chemin complet d'accès à la DLL.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Une fois créée, une procédure stockée étendue doit être ajoutée à à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’aide de **sp_addextendedproc**. Pour plus d’informations, consultez [Ajout d’une procédure stockée étendue à SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Cette procédure ne peut être exécutée que dans la base de données **Master** . Pour exécuter une procédure stockée étendue à partir d’une base de données autre que **Master**, qualifiez le nom de la procédure stockée étendue avec **Master**.  
  
 **sp_addextendedproc** ajoute des entrées à l’affichage catalogue [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) , en inscrivant le nom de la nouvelle procédure stockée étendue avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Elle ajoute également une entrée dans l’affichage catalogue [sys. extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) .  
  
> [!IMPORTANT]  
>  Les DLL existantes qui n'ont pas été inscrites avec leur chemin complet ne fonctionneront plus après une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour corriger le problème, utilisez **sp_dropextendedproc** pour annuler l’inscription de la dll, puis réinscrivez-la avec **sp_addextendedproc**, en spécifiant le chemin d’accès complet.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_addextendedproc**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant ajoute la procédure stockée étendue **xp_hello** .  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
