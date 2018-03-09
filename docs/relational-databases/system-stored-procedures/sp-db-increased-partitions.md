---
title: sp_db_increased_partitions | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f53b20cd54d972ebbe95aa4ed9af90b88f7465b6
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2017
---
# <a name="spdbincreasedpartitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Active ou désactive la prise en charge de 15 000 partitions maximum pour la base de données spécifiée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @dbname=] '*nom_base_de_données*'  
 Nom de la base de données. *dbname* est **sysname** avec une valeur par défaut NULL. Si *dbname* n’est pas spécifié, la base de données en cours est utilisé.  
  
 [ @increased_partitions=] '*increased_partitions*'  
 Active ou désactive la prise en charge de 15 000 partitions sur la base de données spécifiée. *increased_partitions* est **varchar(6)** avec NULL comme valeur par défaut. Les valeurs acceptées sont ON ou TRUE pour activer la prise en charge et OFF ou FALSE pour la désactiver. Si *increased_partitions* n’est pas spécifié, la procédure retourne 1 pour indiquer la prise en charge est activée pour la base de données spécifiée ou 0 pour indiquer la prise en charge est désactivée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER DATABASE sur la base de données spécifiée.  
  
  
