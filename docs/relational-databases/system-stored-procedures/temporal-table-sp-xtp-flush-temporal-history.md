---
title: sp_xtp_flush_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_xtp_flush_temporal_history
- sp_xtp_flush_temporal_history_TSQL
- sys.sp_xtp_flush_temporal_history
- sys.sp_xtp_flush_temporal_history_TSQL
helpviewer_keywords:
- sp_xtp_flush_temporal_history
ms.assetid: 322e3170-93f8-468a-a123-104ce7bd7fad
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3818c2ff4689605ff03660d6ae66bf4d579cb443
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037316"
---
# <a name="spxtpflushtemporalhistory-transact-sql"></a>sp_xtp_flush_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Appelle la tâche de vidage de données pour déplacer des lignes tous validés à partir de la table intermédiaire en mémoire pour la table d’historique sur disque.  

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_xtp_flush_temporal_history @schema_name, @object_name  
  
```  
  
## <a name="arguments"></a>Arguments  
 *@schema_name*  
 Le nom de schéma pour la table actuelle ou temporelle  
  
 *@object_name*  
 Le nom de la table actuelle ou temporelle  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou > 0 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite les autorisations db_owner.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations relatives aux performances des tables temporelles avec contrôle de version par le système à mémoire optimisée](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)  
  
  
