---
title: "R&#233;diger des instructions Transact-SQL internationales | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "écriture d'instructions internationales"
  - "observations à caractère international concernant Transact-SQL"
  - "observations à caractère international [SQL Server], Transact-SQL"
  - "observations à caractère international sur le moteur de base de données [SQL Server], Transact-SQL"
  - "instructions [SQL Server], international"
  - "observations à caractère international sur les bases de données [SQL Server], Transact-SQL"
  - "dates [SQL Server], observations à caractère international"
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# R&#233;diger des instructions Transact-SQL internationales
  Les directives suivantes facilitent la transition d'une langue à l'autre des bases de données et applications de bases de données qui utilisent des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)], ou leur permettent de prendre en charge directement plusieurs langues :  
  
-   Remplacez toutes les utilisations des types de données **char**, **varchar** et **text** par **nchar**, **nvarchar** et **nvarchar(max)**. Vous réglez ainsi le problème de conversion des pages de codes. Pour plus d’informations, consultez [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Lors des comparaisons et opérations sur les mois et jours de la semaine, utilisez la partie numérique de la date plutôt que les chaînes de noms. Selon les paramètres de langue, des noms de mois et de jours de la semaine différents sont retournés. Par exemple, DATENAME(MONTH,GETDATE()) retourne « May » pour l'anglais (États-Unis), « Mai » pour l'allemand et « mai » pour le français. Utilisez à la place une fonction comme DATEPART qui utilise le numéro du mois plutôt que son nom. Utilisez les noms DATEPART lorsque vous générez des ensembles de résultats qui seront affichés par un utilisateur, car les noms de date sont souvent plus clairs qu'une représentation numérique. Pour autant, ne codez aucun élément logique dépendant des noms affichés d'une langue spécifique.  
  
-   Pour spécifier des dates dans des comparaisons ou comme entrées d'instructions INSERT ou UPDATE, utilisez des constantes qui sont interprétées de la même manière, quelle que soit la langue définie :  
  
    -   Les applications ADO, OLE DB et ODBC doivent utiliser les clauses ODBC d'échappement de temps, de date et d'horodateur :  
  
         **{ ts'**yyyy**-***mm***-***dd**hh***:***mm***:***ss*[**.***fff*] **'}** tel que : **{ ts'**1998**-**09**-**24 10**:**02**:**20**' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** tel que : **{ d'**1998**-**09**-**24**'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** tel que : **{ t'**10:02:20**'}**  
  
    -   Les applications qui utilisent d'autres API, ou encore des scripts, des procédures stockées ou des déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)], doivent utiliser les chaînes numériques non séparées. Par exemple, *yyyymmdd* comme 19980924.  
  
    -   Les applications qui utilisent d’autres API, ou encore des scripts, des procédures stockées ou des déclencheurs [!INCLUDE[tsql](../../includes/tsql-md.md)], peuvent également utiliser l’instruction CONVERT avec un paramètre de style explicite pour toutes les conversions entre les types de données **time**, **date**, **smalldate**, **datetime**, **datetime2** et **datetimeoffset** et les types de données de chaînes de caractères. Par exemple, l'instruction suivante est interprétée de la même façon, quels que soient les paramètres de connexion concernant la langue et le format de date :  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Pour plus d’informations, consultez [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
  