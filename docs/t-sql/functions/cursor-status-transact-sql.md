---
title: CURSOR_STATUS (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURSOR_STATUS
- CURSOR_STATUS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], cursors
- CURSOR_STATUS function
- cursors [SQL Server], status information
ms.assetid: 3a4a840e-04f8-43bd-aada-35d78c3cb6b0
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 764198ef1fd0f5b18985d985be894fcadf8fa3ce
ms.contentlocale: fr-fr
ms.lasthandoff: 10/12/2017

---
# <a name="cursorstatus-transact-sql"></a>CURSOR_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Fonction scalaire permettant à l'appelant d'une procédure stockée de déterminer si la procédure a retourné un curseur et un ensemble de résultats pour un paramètre donné.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CURSOR_STATUS   
     (  
          { 'local' , 'cursor_name' }   
          | { 'global' , 'cursor_name' }   
          | { 'variable' , 'cursor_variable' }   
     )  
```  
  
## <a name="arguments"></a>Arguments  
'local'  
Spécifie une constante indiquant que la source du curseur est un nom de curseur local.
  
'*cursor_name*'  
Est le nom du curseur. Un nom de curseur doit suivre les règles applicables aux identificateurs.
  
'global'  
Spécifie une constante indiquant que la source du curseur est un nom de curseur global.
  
'variable'  
Spécifie une constante indiquant que la source du curseur est une variable locale.
  
'*variable_de_curseur*'  
Nom de la variable de curseur. Une variable de curseur doit être définie à l’aide de la **curseur** type de données.
  
## <a name="return-types"></a>Types de retour
**smallint**
  
|Valeur retournée|Nom du curseur|Variable du curseur|  
|---|---|---|
|1|L'ensemble de résultats du curseur comprend au moins une ligne.<br /><br /> Pour les curseurs INSENSITIVE et pilotés par jeux de clés, l'ensemble de résultats comprend au moins une ligne.<br /><br /> Pour les curseurs dynamiques, l'ensemble de résultats peut être vide, ou contenir une ou plusieurs lignes.|Le curseur affecté à cette variable est ouvert.<br /><br /> Pour les curseurs INSENSITIVE et pilotés par jeux de clés, l'ensemble de résultats comprend au moins une ligne.<br /><br /> Pour les curseurs dynamiques, l'ensemble de résultats peut être vide, ou contenir une ou plusieurs lignes.|  
|0|L'ensemble de résultats du curseur est vide.*|Le curseur affecté à cette variable est ouvert mais l'ensemble de résultats est vide.*|  
|-1|Le curseur est fermé.|Le curseur affecté à cette variable est fermé.|  
|-2|Non applicable.|Valeurs possibles :<br /><br /> Aucun curseur n'a été affecté à cette variable OUTPUT lors du précédent appel de la procédure.<br /><br /> Un curseur a été affecté à cette variable OUTPUT lors du précédent appel de la procédure mais il était fermé pendant le déroulement de celle-ci. C'est la raison pour laquelle le curseur est désaffecté et qu'il n'est pas retourné à la procédure d'appel.<br /><br /> Aucun curseur n'est affecté à une variable de curseur déclarée.|  
|-3|Il n'existe aucun curseur portant le nom spécifié.|Il n'existe aucune variable de curseur portant le nom spécifié ou, si c'est le cas, aucun curseur ne lui a encore été affecté.|  
  
* Les curseurs dynamiques ne retournent jamais cette valeur.
  
## <a name="examples"></a>Exemples  
L'exemple suivant utilise la fonction `CURSOR_STATUS` pour afficher l'état d'un curseur avant et après qu'il a été ouvert et fermé.
  
```sql
CREATE TABLE #TMP  
(  
   ii int  
)  
GO  
  
INSERT INTO #TMP(ii) VALUES(1)  
INSERT INTO #TMP(ii) VALUES(2)  
INSERT INTO #TMP(ii) VALUES(3)  
  
GO  
  
--Create a cursor.  
DECLARE cur CURSOR  
FOR SELECT * FROM #TMP  
  
--Display the status of the cursor before and after opening  
--closing the cursor.  
  
SELECT CURSOR_STATUS('global','cur') AS 'After declare'  
OPEN cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Open'  
CLOSE cur  
SELECT CURSOR_STATUS('global','cur') AS 'After Close'  
  
--Remove the cursor.  
DEALLOCATE cur  
  
--Drop the table.  
DROP TABLE #TMP  
  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
After declare
---------------
-1  
  
After Open
----------
1  
  
After Close
-----------
-1
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions de curseur &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  

