---
title: SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT
- SET_QUERY_GOVERNOR_COST_LIMIT_TSQL
- QUERY_GOVERNOR_COST_LIMIT
- QUERY_GOVERNOR_COST_LIMIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET QUERY_GOVERNOR_COST_LIMIT statement
- connections [SQL Server], overriding
- QUERY_GOVERNOR_COST_LIMIT option
- overriding connection values
ms.assetid: 3424bb44-6915-462d-a8d7-fe834af81387
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a96642c6a0dd50ccb8717e84a6defec516196d87
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="set-querygovernorcostlimit-transact-sql"></a>SET QUERY_GOVERNOR_COST_LIMIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Remplace l’actuellement configuré **SET QUERY_GOVERNOR_COST_LIMIT** valeur pour la connexion actuelle.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET QUERY_GOVERNOR_COST_LIMIT value  
```  
  
## <a name="arguments"></a>Arguments  
 *valeur*  
 Valeur numérique ou entière qui spécifie la durée la plus longue pendant laquelle une requête peut s'exécuter. Les valeurs sont arrondies à l'entier le plus proche. Les valeurs négatives sont arrondies à 0. L'Administrateur de requêtes n'autorise pas l'exécution de requêtes dont le coût estimé excède cette valeur. Si vous définissez 0 (valeur par défaut) pour cette option, vous désactivez la fonction de l'administrateur de requêtes, et toutes les requêtes s'exécutent indéfiniment.  
  
 Le « coût d'une requête » correspond à la durée (en secondes) estimée nécessaire à l'exécution complète d'une requête dans une configuration matérielle donnée.  
  
## <a name="remarks"></a>Notes  
 L'utilisation de SET QUERY_GOVERNOR_COST_LIMIT s'applique à la connexion active et est effective durant celle-ci uniquement. Utilisez le [configurer le SET QUERY_GOVERNOR_COST_LIMIT Server Configuration Option](../../database-engine/configure-windows/configure-the-query-governor-cost-limit-server-configuration-option.md)option de **sp_configure** valeur limite de coût pour modifier l’administrateur de requêtes de l’échelle du serveur. Pour plus d’informations sur la configuration de cette option, consultez [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) et [les Options de Configuration de serveur &#40; SQL Server &#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 SET QUERY_GOVERNOR_COST_LIMIT est définie lors de l'exécution, et non pas durant l'analyse.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
