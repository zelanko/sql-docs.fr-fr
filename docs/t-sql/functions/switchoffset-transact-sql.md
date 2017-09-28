---
title: SWITCHOFFSET (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 12/02/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SWITCHTZ
- SWITCHTZ_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- functions [SQL Server], time
- functions [SQL Server], date and time
- SWITCHOFFSET function [SQL Server]
- time [SQL Server], functions
- date and time [SQL Server], SWITCHOFFSET
- time zones [SQL Server]
ms.assetid: 32a48e36-0aa4-4260-9fe9-cae9197d16c5
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 712b6c1b582c2eec76958eafaad5d02f2e411640
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="switchoffset-transact-sql"></a>SWITCHOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne un **datetimeoffset** valeur modifiée à partir du décalage de fuseau horaire stocké à un nouveau décalage de fuseau horaire spécifié.  
  
 Pour une vue d’ensemble de tous les [!INCLUDE[tsql](../../includes/tsql-md.md)] les types de données date et heure et les fonctions, consultez [Date et fonctions et Types de données &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SWITCHOFFSET ( DATETIMEOFFSET, time_zone )   
```  
  
## <a name="arguments"></a>Arguments  
 *DATETIMEOFFSET*  
 Est une expression qui peut être résolue en un **DateTimeOffset (n)** valeur.  
  
 *time_zone*  
 Chaîne de caractères au format [+|-]TZH:TZM ou entier signé (de minutes) qui représente le décalage de fuseau horaire, et qui est supposée être réglée et prendre en charge l'heure d'été.  
  
## <a name="return-type"></a>Type de retour  
 **DateTimeOffset** avec une précision de fractions de seconde le *DATETIMEOFFSET* argument.  
  
## <a name="remarks"></a>Notes  
 Utilisez SWITCHOFFSET pour sélectionner un **datetimeoffset** valeur dans un décalage de fuseau horaire différent à partir du décalage de fuseau horaire a été enregistrée à l’origine. SWITCHOFFSET ne met pas à jour stockées *time_zone* valeur.  
  
 SWITCHOFFSET peut être utilisé pour mettre à jour un **datetimeoffset** colonne.  
  
 L'utilisation de SWITCHOFFSET avec la fonction GETDATE() peut entraîner un ralentissement de l'exécution de la requête. Cela est dû au fait que l'optimiseur de requête n'est pas en mesure d'obtenir les estimations de cardinalité exactes pour la valeur datetime. Pour résoudre ce problème, utilisez l'indicateur de requête OPTION (RECOMPILE) pour forcer l'optimiseur de requête à recompiler un plan de requête lors de la prochaine exécution de cette même requête. L'optimiseur dispose alors d'estimations de cardinalité précises et produit un plan de requête plus efficace. Pour plus d’informations sur l’indicateur de requête RECOMPILE, consultez [indicateurs de requête &#40; Transact-SQL &#41; ](../../t-sql/queries/hints-transact-sql-query.md).  
  
```  
DECLARE @dt datetimeoffset = switchoffset (CONVERT(datetimeoffset, GETDATE()), '-04:00');   
SELECT * FROM t    
WHERE c1 > @dt OPTION (RECOMPILE);  
  
```  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant utilise `SWITCHOFFSET` pour afficher un décalage de fuseau horaire différent de la valeur stockée dans la base de données.  
  
```  
CREATE TABLE dbo.test   
    (  
    ColDatetimeoffset datetimeoffset  
    );  
GO  
INSERT INTO dbo.test   
VALUES ('1998-09-20 7:45:50.71345 -5:00');  
GO  
SELECT SWITCHOFFSET (ColDatetimeoffset, '-08:00')   
FROM dbo.test;  
GO  
--Returns: 1998-09-20 04:45:50.7134500 -08:00  
SELECT ColDatetimeoffset  
FROM dbo.test;  
--Returns: 1998-09-20 07:45:50.7134500 -05:00  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'exemple suivant utilise `SWITCHOFFSET` pour afficher un décalage de fuseau horaire différent de la valeur stockée dans la base de données.  
  
```  
CREATE TABLE dbo.test   
    (  
    ColDatetimeoffset datetimeoffset  
    );  
GO  
INSERT INTO dbo.test   
VALUES ('1998-09-20 7:45:50.71345 -5:00');  
GO  
SELECT SWITCHOFFSET (ColDatetimeoffset, '-08:00')   
FROM dbo.test;  
GO  
--Returns: 1998-09-20 04:45:50.7134500 -08:00  
SELECT ColDatetimeoffset  
FROM dbo.test;  
--Returns: 1998-09-20 07:45:50.7134500 -05:00  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CAST et CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [FUSEAU horaire &AMP; #40 ; Transact-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  



