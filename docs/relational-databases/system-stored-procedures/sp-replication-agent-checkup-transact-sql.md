---
description: sp_replication_agent_checkup (Transact-SQL)
title: sp_replication_agent_checkup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replication_agent_checkup_TSQL
- sp_replication_agent_checkup
helpviewer_keywords:
- sp_replication_agent_checkup
ms.assetid: 50357c2e-71aa-4e13-9e2e-0977a3655cc9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5bcd42ae639fad4b50feb6aac829a39abc9a1cad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485722"
---
# <a name="sp_replication_agent_checkup-transact-sql"></a>sp_replication_agent_checkup (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Contrôle, dans chaque base de données de distribution, les Agents de réplication qui s'exécutent sans avoir enregistré d'historique dans l'intervalle de pulsations spécifié. Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replication_agent_checkup [ [ @heartbeat_interval = ] heartbeat_interval ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @heartbeat_interval = ] 'heartbeat_interval'` Nombre maximal de minutes pendant lesquelles un agent peut se connecter sans enregistrer de message de progression. *heartbeat_interval* est de **type int**, avec une valeur par défaut de 10 minutes.  
  
## <a name="return-code-values"></a>Codet de retour  
 **sp_replication_agent_checkup** génère l’erreur 14151 pour chaque agent qu’il détecte comme suspect. Elle enregistre également un message d'historique d'échec au sujet des Agents.  
  
## <a name="remarks"></a>Notes  
 **sp_replication_agent_checkup** est utilisé dans la réplication d’instantané, la réplication transactionnelle et la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_replication_agent_checkup**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
