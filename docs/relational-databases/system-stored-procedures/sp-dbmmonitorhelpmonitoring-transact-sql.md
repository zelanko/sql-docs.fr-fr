---
description: sp_dbmmonitorhelpmonitoring (Transact-SQL)
title: sp_dbmmonitorhelpmonitoring (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorhelpmonitoring
- sp_dbmmonitorhelpmonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorhelpmonitoring
- database mirroring [SQL Server], monitoring
ms.assetid: a085cf87-269f-454a-a146-21f80a113b72
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dd82681731ab29068c2a951850da9f2ad225742b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548157"
---
# <a name="sp_dbmmonitorhelpmonitoring-transact-sql"></a>sp_dbmmonitorhelpmonitoring (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne la période de mise à jour actuelle.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dbmmonitorhelpmonitoring   
```  
  
## <a name="arguments"></a>Arguments  
 Aucun  
  
## <a name="return-code-values"></a>Codet de retour  
 Aucun  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne la période de mise à jour actuelle, c'est-à-dire le nombre de minutes qui s'écoulent entre les mises à jour de la table d'état de la mise en miroir de bases de données. Cette valeur est comprise entre 1 et 120.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne la période de mise à jour actuelle.  
  
```  
EXEC sp_dbmmonitorhelpmonitoring;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
