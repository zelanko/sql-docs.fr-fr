---
title: ERROR_MESSAGE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
caps.latest.revision: 53
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a49d8e24a71b43ba2f400abfbb71f26fe51386a8
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239219"
---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Cette fonction retourne le texte du message de l’erreur qui a provoqué l’exécution du bloc CATCH d’une construction TRY…CATCH.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar(4000)**  
  
## <a name="return-value"></a>Valeur retournée  
Quand elle est appelée dans un bloc CATCH, la fonction `ERROR_MESSAGE` retourne le texte complet du message d’erreur qui a provoqué l’exécution du bloc `CATCH`. Le texte comprend les valeurs fournies pour tous les paramètres remplaçables (par exemple, les longueurs, les noms d’objets ou les heures).  
  
`ERROR_MESSAGE` retourne NULL quand l’appel a lieu en dehors de l’étendue d’un bloc CATCH.  
  
## <a name="remarks"></a>Notes   
`ERROR_MESSAGE` prend en charge les appels à partir de n’importe quel emplacement dans l’étendue d’un bloc CATCH.  
  
`ERROR_MESSAGE` retourne un message d’erreur pertinent, quel que soit le nombre de fois où elle s’exécute, ou l’emplacement de son exécution dans l’étendue du bloc `CATCH`. Ce comportement contraste avec celui d’une fonction comme @@ERROR, qui retourne uniquement un numéro d’erreur dans l’instruction immédiatement après celle qui a provoqué une erreur.  
  
Dans des blocs `CATCH` imbriqués, `ERROR_MESSAGE` retourne le message d’erreur spécifique à l’étendue du bloc `CATCH` qui a référencé ce bloc `CATCH`. Par exemple, le bloc `CATCH` d’une construction TRY...CATCH externe peut comporter une construction `TRY...CATCH` interne. À l’intérieur de ce bloc `CATCH` interne, `ERROR_MESSAGE` retourne le message de l’erreur qui a appelé le bloc `CATCH` interne. Si `ERROR_MESSAGE` s’exécute dans le bloc `CATCH` externe, elle retourne le message de l’erreur qui a appelé ce bloc `CATCH` externe.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. Utilisation de ERROR_MESSAGE dans un bloc CATCH  
L’exemple suivant montre une instruction `SELECT` qui génère une erreur de division par zéro. Le bloc `CATCH` retourne le message d’erreur.  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorMessage
----------------------------------
Divide by zero error encountered.

(1 row(s) affected)

```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. Utilisation de ERROR_MESSAGE dans un bloc CATCH avec d'autres outils de traitement des erreurs  
L’exemple suivant montre une instruction `SELECT` qui génère une erreur de division par zéro. Outre le message de l’erreur, le bloc `CATCH` retourne des informations relatives à cette erreur.  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure  ErrorLine  ErrorMessage
----------- ------------- ----------- --------------- ---------- ----------------------------------
8134        16            1           NULL            4          Divide by zero error encountered.

(1 row(s) affected)

```
  

