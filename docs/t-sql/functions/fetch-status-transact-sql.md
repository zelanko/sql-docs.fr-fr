---
title: '@@FETCH_STATUS (Transact-SQL) | Documents Microsoft'
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@FETCH_STATUS'
- '@@FETCH_STATUS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- status information [SQL Server], FETCH
- '@@FETCH_STATUS function'
ms.assetid: 93659193-e4ff-4dfb-9043-0c4114921b91
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 59f409ed179d158194e98fa60c910c5b38c8e376
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="fetchstatus-transact-sql"></a>@@FETCH_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne l'état de la dernière instruction FETCH de curseur effectuée sur n'importe quel curseur actuellement ouvert par la connexion.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
@@FETCH_STATUS  
```  
  
## <a name="return-type"></a>Type de retour  
 **entier**  
  
## <a name="return-value"></a>Valeur retournée  
  
|Valeur retournée| Description|  
|------------------|-----------------|  
|0|L'instruction FETCH a réussi.|  
|-1|L'instruction FETCH a échoué ou la ligne se situait au-delà du jeu de résultats.|  
|-2|La ligne recherchée est manquante.|
|-9|Le curseur n’effectue pas une opération d’extraction.|  
  
## <a name="remarks"></a>Notes  
 Étant donné que @@FETCH_STATUS est global pour tous les curseurs sur une connexion, utilisez @@FETCH_STATUS avec soin. Après l’exécution d’une instruction FETCH, le test pour @@FETCH_STATUS doit se produire avant l’exécution d’une autre instruction FETCH sur un autre curseur. La valeur de @@FETCH_STATUS n’est pas défini avant les extractions se sont produites sur la connexion.  
  
 Supposons, par exemple, qu'un utilisateur exécute une instruction FETCH sur un curseur, puis appelle une procédure stockée qui ouvre et traite les résultats pour un autre curseur. Lorsque le contrôle est retourné à partir de la procédure stockée appelée, @@FETCH_STATUS reflète la dernière extraction exécutée dans la procédure stockée, pas l’instruction FETCH exécutée avant l’appel de la procédure stockée.  
  
 Pour récupérer le dernier état d’extraction d’un curseur spécifique, interrogez la **fetch_status** colonne de la **sys.dm_exec_cursors** fonction de gestion dynamique.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `@@FETCH_STATUS` pour contrôler les activités d'un curseur dans une boucle `WHILE`.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT BusinessEntityID, JobTitle  
FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de curseur &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)   
 [EXTRACTION &#40; Transact-SQL &#41;](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  

