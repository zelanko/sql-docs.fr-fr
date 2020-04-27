---
title: Rédiger des instructions Transact-SQL internationales | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 64dc9129373a57de2924b2983e14266a67d4915e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62873524"
---
# <a name="write-international-transact-sql-statements"></a>Rédiger des instructions Transact-SQL internationales
  Les directives suivantes facilitent la transition d'une langue à l'autre des bases de données et applications de bases de données qui utilisent des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] , ou leur permettent de prendre en charge directement plusieurs langues :  
  
-   Remplacez toutes les utilisations des types de données `char`, `varchar`, et `text` par `nchar`, `nvarchar`, et `nvarchar(max)`. Vous réglez ainsi le problème de conversion des pages de codes. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](collation-and-unicode-support.md).  
  
-   Lors des comparaisons et opérations sur les mois et jours de la semaine, utilisez la partie numérique de la date plutôt que les chaînes de noms. Selon les paramètres de langue, des noms de mois et de jours de la semaine différents sont retournés. Par exemple, DATENAME(MONTH,GETDATE()) retourne « May » pour l'anglais (États-Unis), « Mai » pour l'allemand et « mai » pour le français. Utilisez à la place une fonction comme DATEPART qui utilise le numéro du mois plutôt que son nom. Utilisez les noms DATEPART lorsque vous générez des ensembles de résultats qui seront affichés par un utilisateur, car les noms de date sont souvent plus clairs qu'une représentation numérique. Pour autant, ne codez aucun élément logique dépendant des noms affichés d'une langue spécifique.  
  
-   Pour spécifier des dates dans des comparaisons ou comme entrées d'instructions INSERT ou UPDATE, utilisez des constantes qui sont interprétées de la même manière, quelle que soit la langue définie :  
  
    -   Les applications ADO, OLE DB et ODBC doivent utiliser les clauses ODBC d'échappement de temps, de date et d'horodateur :  
  
         **{ts'** yyyy**-**_mm_**-**_DDHH_**:**_mm_**:**_SS_[**.** _fff_] **'}** par exemple : **{ts'** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **'}**  
  
         **{ d'** _yyyy_ **-** _mm_ **-** _dd_ **'}** tel que : **{ d'** 1998**-** 09**-** 24 **'}**  
  
         **{t'** _hh_ **:** _mm_ **:** _SS_ **'}** tel que : **{t'** 10:02:20 **'}**  
  
    -   Les applications qui utilisent d'autres API, ou encore des scripts, des procédures stockées ou des déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)] , doivent utiliser les chaînes numériques non séparées. Par exemple, *yyyymmdd* comme 19980924.  
  
    -   Les applications qui utilisent d’autres API [!INCLUDE[tsql](../../includes/tsql-md.md)] , ou des scripts, des procédures stockées et des déclencheurs doivent utiliser l’instruction CONVERT avec un paramètre de style explicite pour toutes `time`les `date`conversions entre les types de données `smalldate`,, `datetime`,, **datetime2** `datetimeoffset` et de type chaîne de caractères. Par exemple, l'instruction suivante est interprétée de la même façon, quels que soient les paramètres de connexion concernant la langue et le format de date :  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Pour plus d’informations, consultez [CAST et CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
  
