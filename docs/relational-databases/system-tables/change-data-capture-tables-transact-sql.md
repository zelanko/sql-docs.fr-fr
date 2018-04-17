---
title: Modifier des Tables de Capture de données (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a4372d0b-50ca-4e58-80f6-2ed3cb52a84a
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 47703a0cb953c5195ee8a8c463669b6ad2cd9163
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="change-data-capture-tables-transact-sql"></a>Tables de capture des données modifiées (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La capture de données modifiées active le suivi des modifications sur les tables afin que les modifications du langage de manipulation de données (DML) et du langage de définition de données (DDL) apportées aux tables puissent être chargées de façon incrémentielle dans un entrepôt de données. Les rubriques de cette section décrivent les tables système qui stockent les informations utilisées par les opérations de capture de données modifiées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [cdc.<capture_instance>_CT](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
 Retourne une ligne pour chaque modification apportée à une colonne capturée dans la table source associée.  
  
 [cdc.captured_columns](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
 Retourne une ligne pour chaque colonne suivie dans une instance de capture.  
  
 [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
 Retourne une ligne pour chaque table de modifications de la base de données.  
  
 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)  
 Retourne une ligne pour chaque modification du langage de définition de données (DDL) apportée aux tables qui sont activées pour la capture des données modifiées.  
  
 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)  
 Retourne une ligne pour chaque transaction qui a des lignes dans une table de modifications. Cette table est utilisée pour le mappage entre les valeurs de validation du numéro séquentiel dans le journal et l'heure de validation de la transaction.  
  
 [cdc.index_columns](../../relational-databases/system-tables/cdc-index-columns-transact-sql.md)  
 Retourne une ligne pour chaque colonne d'index associée à une table de modifications.  
  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
 Retourne les paramètres de configuration pour les travaux de l'agent de capture des données modifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de capture des données modifiées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [Modifier les fonctions de Capture de données &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)  
  
  
