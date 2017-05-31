---
title: "Types de données pris en charge pour l’OLTP en mémoire | Microsoft Docs"
ms.custom: 
ms.date: 05/27/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a928c1f77586198fd0d33cafa445ea406a437c6b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="supported-data-types-for-in-memory-oltp"></a>Types de données pris en charge pour l’OLTP en mémoire
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cet article répertorie les types de données non pris en charge pour les fonctionnalités OLTP en mémoire des éléments suivants :  
  
-   Tables optimisées en mémoire  
  
-   Procédures stockées compilées en mode natif  
  
## <a name="unsupported-data-types"></a>Types de données non pris en charge  
 Les types de données suivants ne sont pas pris en charge.  
  
||||  
|-|-|-|  
|[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)|[geography &#40;Transact-SQL&#41;](../../t-sql/spatial-geography/spatial-types-geography.md)|[geometry &#40;Transact-SQL&#41;](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md)|  
|[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[rowversion &#40;Transact-SQL&#41;](../../t-sql/data-types/rowversion-transact-sql.md)|[xml &#40;Transact-SQL&#41;](../../t-sql/xml/xml-transact-sql.md)|  
|[sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)|Types définis par l'utilisateur|.|  
  
## <a name="notable-supported-data-types"></a>Types de données remarquables pris en charge  
 La plupart des types de données sont pris en charge par les fonctionnalités de l’OLTP en mémoire. Les quelques éléments suivants sont particulièrement intéressants :  
  
|Types binaires et de chaîne|Informations supplémentaires|  
|-----------------------------|--------------------------|  
|binary et varbinary*|[binary et varbinary &#40;Transact-SQL&#41;](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|char et varchar*|[char et varchar &#40;Transact-SQL&#41;](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|nchar et nvarchar*|[nchar et nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
  
Pour les types de données de chaîne et binaires précédents, à partir de SQL Server 2016 :  
  
- Une table optimisée en mémoire individuelle peut également présenter plusieurs colonnes longues, telles que `nvarchar(4000)`, dont la longueur peut même dépasser la taille physique des lignes de 8 060 octets.  
  
- Une table optimisée en mémoire peut afficher des colonnes de type chaîne et binaire de longueur maximale pour les types de données tels que `varchar(max)`.  


### <a name="identify-lobs-and-other-columns-that-are-off-row"></a>Identifier des objets LOB et d’autres colonnes qui sont hors ligne

L’instruction Transact-SQL SELECT suivante signale toutes les colonnes qui sont hors ligne pour des tables optimisées en mémoire. Sachez que :

- Toutes les colonnes de clés d’index sont stockées dans la ligne.
  - Les clés d’index non unique peuvent maintenant inclure des colonnes autorisant les valeurs Null sur des tables optimisées en mémoire.
  - Les index peuvent être déclarés comme uniques sur une table optimisée en mémoire.
- Toutes les colonnes LOB sont stockées hors ligne.
- Une valeur max_length égale à -1 indique une colonne LOB.


```tsql
SELECT
        OBJECT_NAME(m.object_id) as [table],
        c.name                   as [column],
        c.max_length
    FROM
             sys.memory_optimized_tables_internal_attributes AS m
        JOIN sys.columns                                     AS c
                ON  m.object_id = c.object_id
                AND m.minor_id  = c.column_id
    WHERE
        m.type = 5;
```


#### <a name="natively-compiled-modules-support-for-lobs"></a>Les modules compilés en mode natif prennent en charge les objets LOB


Quand vous utilisez une fonction de chaîne intégrée dans des modules compilés en mode natif, par exemple une procédure native, la fonction peut accepter un type LOB de chaîne. Par exemple, dans une procédure native, la fonction LTrim peut entrer un paramètre de type nvarchar(max) ou varbinary(max).

Ces objets LOB peuvent constituer le type de retour d’une fonction définie par l’utilisateur scalaire compilée en mode natif.


### <a name="other-data-types"></a>Autres types de données


|Autres types|Informations supplémentaires|  
|-----------------|--------------------------|  
|types de tables|[Variables de table optimisée en mémoire](http://msdn.microsoft.com/library/bd102e95-53e2-4da6-9b8b-0e4f02d286d3)|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge d'OLTP en mémoire par Transact-SQL](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   
 [Implémentation de colonnes LOB dans une table optimisée en mémoire](http://msdn.microsoft.com/en-us/bd8df0a5-12b9-4f4c-887c-2fb78dd79f4e)   
 [Implémentation de SQL_VARIANT dans une table optimisée en mémoire](../../relational-databases/in-memory-oltp/implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  

