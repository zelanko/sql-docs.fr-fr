---
title: sp_helpextendedproc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpextendedproc
- sp_helpextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpextendedproc
ms.assetid: 7e1f017e-c898-4225-b375-6a73ef9aac7b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7866b9d64a6064cac23382ea3bb33f4fc355cd80
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733211"
---
# <a name="sp_helpextendedproc-transact-sql"></a>sp_helpextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Indique les procédures stockées étendues actuellement définies, ainsi que le nom de la bibliothèque de liaison dynamique (DLL) à laquelle la procédure (fonction) appartient.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilisez plutôt l' [intégration du CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpextendedproc [ [@funcname = ] 'procedure' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @funcname = ] 'procedure'`Nom de la procédure stockée étendue pour laquelle les informations sont signalées. *procedure* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom de la procédure stockée étendue.|  
|**dll**|**nvarchar(255)**|Nom de la DLL.|  
  
## <a name="remarks"></a>Remarques  
 Si vous spécifiez la *procédure* , **sp_helpextendedproc** signale la procédure stockée étendue spécifiée. Lorsque ce paramètre n’est pas fourni, **sp_helpextendedproc** retourne tous les noms de procédures stockées étendues et les noms de dll auxquels appartient chaque procédure stockée étendue.  
  
## <a name="permissions"></a>Autorisations  
 L’autorisation d’exécuter **sp_helpextendedproc** est accordée à **public**.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-reporting-help-on-all-extended-stored-procedures"></a>R. Indication d'aide sur toutes les procédures stockées étendues  
 L'exemple suivant vous renseigne sur toutes les procédures stockées étendues.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc;  
GO  
```  
  
### <a name="b-reporting-help-on-a-single-extended-stored-procedure"></a>B. Indication d'aide sur une procédure stockée étendue  
 L’exemple suivant signale la `xp_cmdshell` procédure stockée étendue.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc xp_cmdshell;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
