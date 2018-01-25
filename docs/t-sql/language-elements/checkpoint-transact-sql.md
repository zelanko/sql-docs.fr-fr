---
title: CHECKPOINT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHECKPOINT_TSQL
- CHECKPOINT
dev_langs: TSQL
helpviewer_keywords:
- events [SQL Server], checkpoints
- automatic checkpoints
- writing dirty pages to disk
- pages [SQL Server], dirty
- checkpoints [SQL Server]
- CHECKPOINT statement
- log truncate mode [SQL Server]
- dirty pages
- logs [SQL Server], checkpoints
- manual checkpoints [SQL Server]
- pages [SQL Server], checkpoints
ms.assetid: ccdfc689-ad4e-44c0-83f7-0f2cfcfb6406
caps.latest.revision: "59"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6353bd534827ff9066bd7b184a09d67b5867c3cb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="checkpoint-transact-sql"></a>CHECKPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Génère un point de contrôle manuel dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous êtes connecté.  
  
> [!NOTE]  
>  Pour plus d’informations sur les différents types de points de contrôle de base de données et l’opération de point de contrôle en général, consultez [points de contrôle de base de données &#40; SQL Server &#41; ](../../relational-databases/logs/database-checkpoints-sql-server.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CHECKPOINT [ checkpoint_duration ]  
```  
  
## <a name="arguments"></a>Arguments  
 *checkpoint_duration*  
 Spécifie le temps requis (en secondes) pour terminer le point de contrôle manuel. Lorsque *checkpoint_duration* est spécifié, le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] tente d’effectuer le point de contrôle au sein de la durée demandée. Le *checkpoint_duration* doit être une expression de type **int** et doit être supérieure à zéro. Lorsque ce paramètre est omis, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] règle la durée du point de contrôle pour minimiser l'impact sur les performances des applications de base de données. *checkpoint_duration* est une option avancée.  
  
## <a name="factors-affecting-the-duration-of-checkpoint-operations"></a>Facteurs ayant une incidence sur la durée des opérations de point de contrôle  
 En règle générale, le temps nécessaire à la réalisation d'un point de contrôle augmente avec le nombre de pages incorrectes à écrire. Par défaut, pour réduire l'impact sur les performances sur d'autres applications, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ajuste la fréquence des écritures qu'une opération de point de contrôle effectue. La diminution de la fréquence d'écriture augmente la durée de l'opération de point de contrôle. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]utilise cette stratégie pour un point de contrôle manuel, sauf si un *checkpoint_duration* valeur est spécifiée dans la commande CHECKPOINT.  
  
 L’impact sur les performances de l’utilisation de *checkpoint_duration* dépend du nombre de pages incorrectes, l’activité sur le système et la durée réelle spécifiée. Par exemple, si le point de contrôle s’effectue normalement en 120 secondes, en spécifiant un *checkpoint_duration* de 45 secondes oblige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consacrer davantage de ressources pour le point de contrôle que ce qui serait attribué par défaut. En revanche, en spécifiant un *checkpoint_duration* de 180 secondes provoquerait [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour affecter le moins de ressources doivent être affectées par défaut. En général, un court *checkpoint_duration* augmente les ressources attribuées au point de contrôle, tandis qu’une durée *checkpoint_duration* permet de réduire les ressources attribuées au point de contrôle. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue toujours un point de contrôle lorsque cela est possible et l'instruction CHECKPOINT renvoie immédiatement les informations lorsqu'un point de contrôle se termine. Ainsi, dans certains cas, un point de contrôle peut se terminer avant ou après que la durée spécifiée soit écoulée.  
  
##  <a name="Security"></a> Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Autorisations de point de contrôle par défaut aux membres de la **sysadmin** rôle serveur fixe et le **db_owner** et **db_backupoperator** des rôles de base de données fixe et ne sont pas transférables.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Points de contrôle de base de données &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Configurer l’Option de Configuration de serveur recovery interval](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)   
 [SHUTDOWN &#40;Transact-SQL&#41;](../../t-sql/language-elements/shutdown-transact-sql.md)  
  
  
