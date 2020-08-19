---
description: sysmail_help_status_sp (Transact-SQL)
title: sysmail_help_status_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_status_sp
- sysmail_help_status_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_status_sp
ms.assetid: b44277c6-81e8-4b4d-85b3-a2f04d602e7a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 53f0512a2d6d57606a146c39325692b9c3d351e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469167"
---
# <a name="sysmail_help_status_sp-transact-sql"></a>sysmail_help_status_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Affiche l'état des files d'attente de la messagerie de base de données. Utilisez **sysmail_start_sp** pour démarrer les files d’attente d’Database Mail et **sysmail_stop_sp** pour arrêter les files d’attente de Database mail.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_status_sp  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-set"></a>Jeu de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**État**|**nvarchar (7)**|État de la messagerie de base de données. Les valeurs possibles sont **Started** et **Stopped**.|  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, seuls les membres du rôle serveur fixe **sysadmin** peuvent accéder à cette procédure.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant affiche l'état de la messagerie de base de données.  
  
```  
EXECUTE msdb.dbo.sysmail_help_status_sp ;  
GO  
```  
  
 Jeu de résultats :  
  
```  
Status  
-------  
STARTED  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programme externe Database Mail](../../relational-databases/database-mail/database-mail-external-program.md)   
 [sysmail_start_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [sysmail_stop_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)  
  
  
