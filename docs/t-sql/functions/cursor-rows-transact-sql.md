---
title: '@@CURSOR_ROWS (Transact-SQL) | Microsoft Docs'
ms.custom: 
ms.date: 08/18/2017
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
- '@@CURSOR_ROWS'
- '@@CURSOR_ROWS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CURSOR_ROWS function'
- cursors [SQL Server], last-opened
- last-opened cursor
- asynchronous cursors [SQL Server]
ms.assetid: 31bd7a97-7f28-42a8-ba24-24d16d22973d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8c4c1fac4c5d9dacddfb942a3e5b9238e5be16a4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40cursorrows-transact-sql"></a>&#x40;&#x40;CURSOR_ROWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne le nombre de lignes éligibles se trouvant actuellement dans le dernier curseur ouvert sur la connexion. Afin d'améliorer les performances, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut charger de grands curseurs pilotés par jeux de clés et curseurs statiques de manière asynchrone. @@CURSOR_ROWS peut être appelé pour déterminer que le nombre de lignes éligibles pour un curseur sont extraites au moment de l’appel de @@CURSOR_ROWS.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```
@@CURSOR_ROWS  
```  
  
## <a name="return-types"></a>Types de retour
**entier**
  
## <a name="return-value"></a>Valeur retournée  
  
|Valeur retournée|Description|  
|---|---|
|-*m*|Le curseur est rempli de façon asynchrone. La valeur retournée (-*m*) correspond au nombre de lignes figurant actuellement dans le jeu de clés.|  
|-1|Le curseur est dynamique. Puisque les curseurs dynamiques reflètent toutes les modifications, le nombre de lignes qui se qualifient pour le curseur varie constamment. On ne peut jamais affirmer définitivement que toutes les lignes qualifiées ont été extraites.|  
|0|Aucun curseur n'a été ouvert, aucune ligne n'a été qualifiée pour le dernier curseur ouvert ou le dernier curseur ouvert est fermé ou désalloué.|  
|*n*|Le curseur est totalement rempli. La valeur retournée (*n*) correspond au nombre total de lignes du curseur.|  
  
## <a name="remarks"></a>Notes   
Le nombre retourné par @@CURSOR_ROWS est négatif si le dernier curseur a été ouvert de façon asynchrone. Les curseurs pilotés par jeux de clés ou les curseurs statiques sont ouverts de façon asynchrone si la valeur du seuil du curseur de sp_configure est supérieure à 0 et si le nombre de lignes du jeu de résultats du curseur est supérieur au seuil du curseur.
  
## <a name="examples"></a>Exemples  
L'exemple suivant déclare un curseur et utilise `SELECT` pour afficher la valeur de `@@CURSOR_ROWS`. La valeur du paramètre est `0` avant l'ouverture du curseur, et `-1` pour indiquer que le jeu de clés du curseur est rempli de façon asynchrone.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@CURSOR_ROWS;  
DECLARE Name_Cursor CURSOR FOR  
SELECT LastName ,@@CURSOR_ROWS FROM Person.Person;  
OPEN Name_Cursor;  
FETCH NEXT FROM Name_Cursor;  
SELECT @@CURSOR_ROWS;  
CLOSE Name_Cursor;  
DEALLOCATE Name_Cursor;  
GO             
```  
  
Voici les jeux de résultats obtenus.
  
```
-----------
0  
```

```
LastName
---------------
Sanchez
```

```
-----------
-1
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions de curseur &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)  
[OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)
  
  
