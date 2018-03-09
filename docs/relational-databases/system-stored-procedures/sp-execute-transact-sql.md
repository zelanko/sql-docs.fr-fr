---
title: sp_execute (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cursor_execute
- sp_cursor_execute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute
ms.assetid: 2009acd3-0d92-435a-a8fb-057e50dc7146
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2b40bd51a730cf902068aa0ba8bc40411f002f3b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spexecute-transact-sql"></a>sp_execute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Exécute une commande préparée [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction à l’aide d’un handle spécifié et la valeur du paramètre facultatif. sp_execute est appelée en spécifiant ID = 12 dans un paquet de stream (TDS) de données tabulaires.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_execute handle OUTPUT  
    [,bound_param  ]  [,...n ]  ]  
```  
  
## <a name="arguments"></a>Arguments  
 *handle*  
 Est la *gérer* valeur retournée par sp_prepare. *gérer les* est un paramètre obligatoire qui demande **int** valeur d’entrée.  
  
 *bound_param*  
 Indique l'utilisation de paramètres supplémentaires. *bound_param* est un paramètre obligatoire qui requiert des valeurs d’entrée de tout type de données pour indiquer des paramètres supplémentaires pour la procédure.  
  
> [!NOTE]  
>  *bound_param* doivent correspondre aux déclarations effectuées par le sp_prepare*params* valeur et peut être sous la forme  *@name = valeur* ou *valeur*.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_prepare &#40; Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)  
  
  
