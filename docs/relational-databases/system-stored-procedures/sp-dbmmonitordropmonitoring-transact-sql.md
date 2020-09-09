---
description: sp_dbmmonitordropmonitoring (Transact-SQL)
title: sp_dbmmonitordropmonitoring (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitordropmonitoring_TSQL
- sp_dbmmonitordropmonitoring
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitordropmonitoring
- database mirroring [SQL Server], monitoring
ms.assetid: 6f2d552d-bfd7-47a5-8dcb-05560aa1a32d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c7ef235d29ea317a4e6e1b7967808d4ac135f801
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89536564"
---
# <a name="sp_dbmmonitordropmonitoring-transact-sql"></a>sp_dbmmonitordropmonitoring (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Arrête et supprime le travail de surveillance de la mise en miroir pour toutes les bases de données sur l'instance du serveur.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dbmmonitordropmonitoring   
```  
  
## <a name="arguments"></a>Arguments  
 Aucun  
  
## <a name="return-code-values"></a>Codet de retour  
 Aucun  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la surveillance de la mise en miroir de bases de données pour toutes les bases de données en miroir sur l'instance du serveur.  
  
```  
EXEC sp_dbmmonitordropmonitoring ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitoraddmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitoraddmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
