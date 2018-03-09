---
title: SESSION_ID (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 2a0d500a-f6c8-490f-9abd-3ae824986404
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07c52331f64cd9104deb8956b893cc2759371feb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="sessionid-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne l’ID d’actuel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] session.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **nvarchar(32)** valeur.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 L’ID de session est attribué à chaque connexion utilisateur lors de la connexion est établie. Il persiste pendant la durée de la connexion. Lorsque la connexion se termine, l’ID de session est publié.  
  
 L’ID de session commence par les caractères alphabétiques 'SID'. Ils respectent la casse et doit être en majuscule lorsque l’ID de session est utilisée dans [!INCLUDE[DWsql](../../includes/dwsql-md.md)] commandes.  
  
 Vous pouvez interroger l’affichage [sys.dm_pdw_exec_sessions](http://msdn.microsoft.com/en-us/5b656c55-427f-4306-8bd9-9d7987c203d9) pour extraire les mêmes informations que cette fonction.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne l’ID de session active.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSION &#40; Entrepôt de données SQL &#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
