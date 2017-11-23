---
title: OPEN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPEN_TSQL
- OPEN
dev_langs: TSQL
helpviewer_keywords:
- opening cursors
- cursors [SQL Server], opening
- populating cursors [SQL Server]
- OPEN statement
- Transact-SQL cursors, opening
ms.assetid: fd1c5e3b-6045-4a42-b646-3fca76e874c1
caps.latest.revision: "36"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: aec83ff9ef56b4d4ae02867d4055d0b1e38f41ec
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="open-transact-sql"></a>OPEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ouvre un [!INCLUDE[tsql](../../includes/tsql-md.md)] curseur côté serveur et remplit le curseur en exécutant la [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction spécifiée dans l’instruction DECLARE CURSOR ou d’un ensemble *variable_de_curseur* instruction.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPEN { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>Arguments  
 GLOBAL  
 Spécifie que *cursor_name* fait référence à un curseur global.  
  
 *tous les autres cas*  
 Représente le nom d'un curseur déclaré. Si un global et un curseur local portent *cursor_name* comme leur nom, *cursor_name* fait référence au curseur global si GLOBAL est spécifié ; sinon, *cursor_name* fait référence au curseur local.  
  
 *nom_de_variable_de_curseur*  
 Nom d'une variable de curseur faisant référence à un curseur.  
  
## <a name="remarks"></a>Notes  
 Si le curseur est déclaré avec l'option INSENSITIVE ou STATIC, OPEN crée une table temporaire pour recueillir l'ensemble de résultats. OPEN échoue si la longueur d'une ligne de l'ensemble de résultats est supérieure à la longueur de ligne maximale des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le curseur est déclaré avec l'option KEYSET, OPEN crée une table temporaire pour recueillir le jeu de clés. Les tables temporaires sont stockées dans tempdb.  
  
 Une fois un curseur a été ouvert, utilisez le @@CURSOR_ROWS fonction à recevoir le nombre de qualifier les lignes dans le dernier curseur ouvert.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge la génération asynchrone de curseurs [!INCLUDE[tsql](../../includes/tsql-md.md)] pilotés par jeux de clés ou statiques. [!INCLUDE[tsql](../../includes/tsql-md.md)] sur les curseurs telles que OPEN ou FETCH sont exécutées par lot : la génération asynchrone de curseurs [!INCLUDE[tsql](../../includes/tsql-md.md)] n'est donc pas nécessaire. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] continue de prendre en charge les curseurs côté serveur d’API pilotés par jeux de clés ou statiques asynchrones si l’opération de curseur OPEN présente une latence trop faible, en raison des boucles clientes de chaque opération de curseur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant ouvre un curseur et extrait toutes les lignes.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT LastName, FirstName  
FROM AdventureWorks2012.HumanResources.vEmployee  
WHERE LastName like 'B%';  
  
OPEN Employee_Cursor;  
  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    FETCH NEXT FROM Employee_Cursor  
END;  
  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fermer &#40; Transact-SQL &#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [@@CURSOR_ROWS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-rows-transact-sql.md)   
 [DÉSALLOUER &#40; Transact-SQL &#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [EXTRACTION &#40; Transact-SQL &#41;](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  
