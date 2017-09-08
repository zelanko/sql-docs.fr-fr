---
title: CLOSE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE_TSQL
- CLOSE
dev_langs:
- TSQL
helpviewer_keywords:
- closing cursors
- cursors [SQL Server], closing
- CLOSE statement
ms.assetid: 21546874-97e3-4b93-970f-87c27f6b78c7
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7315b45fa3b13b96fa01c7833ed1370f72e4bab8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="close-transact-sql"></a>CLOSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ferme un curseur ouvert en libérant le jeu de résultats actuel et tous les verrous de curseur dans les lignes sur lesquelles le curseur est positionné. L'instruction CLOSE garde les structures de données disponibles pour une réouverture éventuelle, mais les extractions et les mises à jour positionnées ne sont pas autorisées jusqu'à la réouverture du curseur. L'instruction CLOSE doit être exécutée sur un curseur ouvert. Elle n'est pas autorisée sur un curseur qui a seulement été déclaré ou qui est déjà fermé.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CLOSE { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>Arguments  
 GLOBAL  
 Spécifie que *cursor_name* fait référence à un curseur global.  
  
 *tous les autres cas*  
 Nom d'un curseur ouvert. Si un global et un curseur local portent *cursor_name* comme leur nom, *cursor_name* fait référence au curseur global si GLOBAL est spécifié ; sinon, *cursor_name* fait référence au curseur local.  
  
 *nom_de_variable_de_curseur*  
 Nom d'une variable de curseur associée à un curseur ouvert.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre comment positionner correctement l'instruction `CLOSE` dans un processus basé sur un curseur.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT EmployeeID, Title FROM AdventureWorks2012.HumanResources.Employee;  
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
 [Curseurs](../../relational-databases/cursors.md)   
 [Curseurs &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DÉSALLOUER &#40; Transact-SQL &#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [EXTRACTION &#40; Transact-SQL &#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [Ouvrir &#40; Transact-SQL &#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
