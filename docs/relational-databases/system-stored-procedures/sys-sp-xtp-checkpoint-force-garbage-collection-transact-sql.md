---
description: sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL)
title: sys. sp_xtp_checkpoint_force_garbage_collection (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_checkpoint_force_garbage_collection_TSQL
- sys.sp_xtp_checkpoint_force_garbage_collection
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_checkpoint_force_garbage_collection
ms.assetid: 82b35b2b-edbd-44ac-9fc8-80695f2fd1df
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9073ebd53ea3b2bb87719b92132e2e4e1e38caf5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473413"
---
# <a name="syssp_xtp_checkpoint_force_garbage_collection-transact-sql"></a>sys.sp_xtp_checkpoint_force_garbage_collection (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Marque les fichiers source utilisés dans l'opération de fusion avec le numéro séquentiel dans le journal (LSN) après lequel ils ne sont pas nécessaires et peuvent être récupérés par le garbage collector. En outre, place les fichiers dont le LSN associé est inférieur au point de troncation du journal dans le garbage collection du flux de fichier.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
 
## <a name="syntax"></a>Syntaxe  
  
```  
sys.sp_xtp_checkpoint_force_garbage_collection [[ @dbname=database_name]  
```  
  
## <a name="arguments"></a>Arguments  
 *database_name*  
 Base de données sur laquelle le garbage collection doit être exécuté. La valeur par défaut est la base de données active.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 pour réussite. Une valeur différente de zéro pour un échec.  
  
## <a name="result-set"></a>Jeu de résultats  
 Une ligne retournée contient les informations suivantes :  
  
|Colonne|Description|  
|------------|-----------------|  
|num_collected_items|Indique le nombre de fichiers qui ont été déplacés vers le garbage collection du flux de fichier. Il s'agit des fichiers dont le numéro séquentiel dans le journal (LSN) est inférieur au LSN du point de troncation du journal.|  
|num_marked_for_collection_items|Indique le nombre de fichiers de données/delta dont le LSN a été mis à jour avec le blockID du LSN de fin de journal.|  
|last_collected_xact_seqno|Retourne le dernier LSN correspondant jusqu'auquel les fichiers ont été déplacés vers le garbage collection du flux de fichier.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation de propriétaire de base de données.  
  
## <a name="sample"></a>Exemple  
  
```  
exec [sys].[sp_xtp_checkpoint_force_garbage_collection] hkdb1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
