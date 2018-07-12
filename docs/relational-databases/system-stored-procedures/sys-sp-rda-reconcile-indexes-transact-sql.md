---
title: Sys.sp_rda_reconcile_indexes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rda_reconcile_indexes
- sp_rda_reconcile_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_indexes stored procedure
ms.assetid: 96b31ab9-bf84-46d6-9990-81f5c51f885a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff2352fde5124f1f0db140914799f2a6d75f88d8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431918"
---
# <a name="syssprdareconcileindexes-transact-sql"></a>Sys.sp_rda_reconcile_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Files d’attente d’une tâche de schéma pour réconcilier les index sur la table distante. Une fois cette tâche terminée avec succès, la table distante a les mêmes index qui existent sur la table compatible Stretch locale.  
  
 S’il existe une autre tâche en file d’attente pour réconcilier les index lorsque vous appelez **sp_rda_reconcile_indexes**, cette procédure stockée n’en file d’attente une tâche en double.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>Arguments  
 [@objname =] *'nom_d ' objet'*  
 Est le nom qualifié ou non qualifié de la table compatible Stretch pour lequel vous souhaitez réconcilier les index. Guillemets sont requis uniquement si vous spécifiez un objet qualifié.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou >0 (échec)  
  
## <a name="see-also"></a>Voir aussi  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
