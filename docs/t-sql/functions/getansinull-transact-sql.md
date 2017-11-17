---
title: GETANSINULL (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GETANSINULL
- GETANSINULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], default
- GETANSINULL function
- default nullability
- database nullability [SQL Server]
ms.assetid: 189399e4-428d-4902-b3a8-94f07fdefc6a
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a103d3d4cc1c66bfcfe47decd4366b47d7831e8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="getansinull-transact-sql"></a>GETANSINULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la possibilité de valeur NULL par défaut de la base de données pour cette session.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GETANSINULL ( [ 'database' ] )  
```  
  
## <a name="arguments"></a>Arguments  
 '*base de données*'  
 Nom de la base de données pour laquelle retourner des informations sur les possibilités de valeur NULL. *base de données*est **char** ou **nchar**. Si **char**, *base de données* est implicitement converti en **nchar**.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 Lorsque la possibilité de valeur NULL de la base de données précisée autorise les valeurs NULL et que la possibilité de valeur NULL de la colonne et du type de données n'est pas définie explicitement, GETANSINULL retourne 1. Il s'agit de la valeur par défaut ANSI NULL.  
  
 Pour activer le comportement par défaut de ANSI NULL, l'une des conditions suivantes doit être définie :  
  
-   ALTER DATABASE *nom_base_de_données* SET des ON ANSI_NULL_DEFAULT  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET ANSI_NULL_DFLT_OFF OFF  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne la possibilité de valeur NULL par défaut pour la base de données `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT GETANSINULL('AdventureWorks2012')  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------  
1  

(1 row(s) affected)
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions système &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

