---
title: Fonctions déterministes et non déterministes | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- built-in functions [SQL Server]
- nondeterministic functions
- extended stored procedures [SQL Server], functions that call
- deterministic functions
- user-defined functions [SQL Server], deterministic
ms.assetid: 2f3ce5f5-c81c-4470-8141-8144d4f218dd
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7df37d9b9339ef98e438e15678c0781df2875a18
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247256"
---
# <a name="deterministic-and-nondeterministic-functions"></a>Fonctions déterministes et non déterministes
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Les fonctions déterministes retournent toujours le même résultat quel que soit le moment auquel elles sont appelées avec un ensemble spécifique de valeurs d'entrée et sur la base du même état de la base de données. Les fonctions non déterministes peuvent retourner différents résultats chaque fois qu'elles sont appelées avec un ensemble spécifique de valeurs d'entrée, même si l'état de la base de données à laquelle elles accèdent demeure inchangé. Par exemple, la fonction AVG retourne toujours le même résultat pour les conditions ci-dessus, mais la fonction GETDATE, qui retourne la valeur datetime actuelle, retourne toujours un résultat différent.  
  
 Plusieurs propriétés de fonctions définies par l’utilisateur déterminent la possibilité pour le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] d’indexer les résultats d’une fonction, par le biais d’index sur des colonnes calculées qui appellent la fonction, ou de vues indexées qui y font référence. Le déterminisme d'une fonction est l'une de ces propriétés. Par exemple, un index cluster ne peut pas être créé sur une vue si celle-ci fait référence à une fonction non déterministe. Pour plus d’informations sur les propriétés des fonctions, dont le déterminisme, consultez [Fonctions définies par l’utilisateur](../../relational-databases/user-defined-functions/user-defined-functions.md).  
  
 Cette rubrique identifie le déterminisme des fonctions système intégrées, ainsi que l'effet sur la propriété déterministe des fonctions définies par l'utilisateur lorsqu'elle contient un appel à des procédures stockées étendues.  
  
## <a name="built-in-function-determinism"></a>Déterminisme des fonctions intégrées  
 Vous ne pouvez pas influer sur le déterminisme d'une fonction intégrée. Chaque fonction intégrée est déterministe ou non déterministe en fonction de son implémentation par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, spécifier une clause ORDER BY dans une requête ne modifie pas le déterminisme d'une fonction utilisée dans cette requête.  
  
 Toutes les fonctions de chaîne intégrées sont déterministes, sauf [FORMAT](../../t-sql/functions/format-transact-sql.md). Pour obtenir la liste de ces fonctions, consultez [Fonctions de chaîne &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md).  
  
 Les fonctions intégrées suivantes, qui ne sont pas des fonctions de chaîne, sont toujours déterministes :  
  
:::row:::
    :::column:::
        ABS
    :::column-end:::
    :::column:::
        DATEDIFF
    :::column-end:::
    :::column:::
        POWER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ACOS
    :::column-end:::
    :::column:::
        DAY
    :::column-end:::
    :::column:::
        RADIANS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ASIN
    :::column-end:::
    :::column:::
        DEGREES
    :::column-end:::
    :::column:::
        ROUND
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ATAN
    :::column-end:::
    :::column:::
        EXP
    :::column-end:::
    :::column:::
        SIGN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ATN2
    :::column-end:::
    :::column:::
        FLOOR
    :::column-end:::
    :::column:::
        SIN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CEILING
    :::column-end:::
    :::column:::
        ISNULL
    :::column-end:::
    :::column:::
        SQUARE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COALESCE
    :::column-end:::
    :::column:::
        ISNUMERIC
    :::column-end:::
    :::column:::
        SQRT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COS
    :::column-end:::
    :::column:::
        LOG
    :::column-end:::
    :::column:::
        TAN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COT
    :::column-end:::
    :::column:::
        LOG10
    :::column-end:::
    :::column:::
        YEAR
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DATALENGTH
    :::column-end:::
    :::column:::
        MONTH
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DATEADD
    :::column-end:::
    :::column:::
        NULLIF
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
 
 Les fonctions suivantes ne sont pas toujours déterministes mais peuvent être utilisées dans les vues indexées ou les index de colonnes calculées si elles sont spécifiées de manière déterministe :  
  
|Fonction|Commentaires|  
|--------------|--------------|  
|Toutes les fonctions d'agrégation|Toutes les fonctions d'agrégation sont déterministes, sauf si elles sont spécifiées avec les clauses OVER et ORDER BY. Pour obtenir la liste de ces fonctions, consultez [Fonctions d’agrégation &#40;Transact-SQL&#41;](../../t-sql/functions/aggregate-functions-transact-sql.md).|  
|CAST|Déterministe sauf si utilisée avec **datetime**, **smalldatetime**ou **sql_variant**.|  
|CONVERT|Déterministe sauf dans l'un des cas suivants :<br /><br /> <br /><br /> Le type de source est **sql_variant**.<br /><br /> Le type de cible est **sql_variant** et son type de source est non déterministe.<br /><br /> Le type de source ou de cible est **datetime** ou **smalldatetime**, l’autre type de source ou de cible est une chaîne de caractères et un style non déterministe est spécifié. Pour être déterministe, le paramètre de style doit être une constante. De plus, les styles inférieurs ou égaux à 100 sont non-déterministes, à l'exception des styles 20 et 21. Les styles supérieurs à 100 sont déterministes, à l'exception des styles 106, 107, 109 et 113.|  
|CHECKSUM|Déterministe, sauf CHECKSUM(*).|  
|ISDATE|Déterministe uniquement si utilisé avec la fonction CONVERT, si le paramètre de style CONVERT est spécifié et si le style est différent de 0, 100, 9 ou 109.|  
|RAND|RAND est déterministe uniquement quand un paramètre *seed* est spécifié.|  
  
 Toutes les fonctions relatives à la configuration, aux curseurs, aux métadonnées, à la sécurité et aux statistiques système sont non déterministes. Pour obtenir la liste de ces fonctions, consultez [Fonctions de configuration &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md), [Fonctions de curseur &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md), [Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md), [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md) et [Fonctions statistiques du système &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md).  
  
 Les fonctions intégrées suivantes, qui appartiennent à d'autres catégories, sont toujours non déterministes.  
  
:::row:::
    :::column:::
        @@CONNECTIONS
    :::column-end:::
    :::column:::
        GETDATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@CPU_BUSY
    :::column-end:::
    :::column:::
        GETUTCDATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@DBTS
    :::column-end:::
    :::column:::
        GET_TRANSMISSION_STATUS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@IDLE
    :::column-end:::
    :::column:::
        LAG
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@IO_BUSY
    :::column-end:::
    :::column:::
        LAST_VALUE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@MAX_CONNECTIONS
    :::column-end:::
    :::column:::
        LEAD
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACK_RECEIVED
    :::column-end:::
    :::column:::
        MIN_ACTIVE_ROWVERSION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACK_SENT
    :::column-end:::
    :::column:::
        NEWID
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACKET_ERRORS
    :::column-end:::
    :::column:::
        NEWSEQUENTIALID
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TIMETICKS
    :::column-end:::
    :::column:::
        NEXT VALUE FOR
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_ERRORS
    :::column-end:::
    :::column:::
        NTILE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_READ
    :::column-end:::
    :::column:::
        PARSENAME
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_WRITE
    :::column-end:::
    :::column:::
        PERCENTILE_CONT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        AT TIME ZONE
    :::column-end:::
    :::column:::
        PERCENTILE_DISC
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        CUME_DIST
    :::column-end:::
    :::column:::
        PERCENT_RANK
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CURRENT_TIMESTAMP
    :::column-end:::
    :::column:::
        RAND
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DENSE_RANK
    :::column-end:::
    :::column:::
        RANK
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        FIRST_VALUE
    :::column-end:::
    :::column:::
        ROW_NUMBER
    :::column-end:::
:::row-end:::   
:::row:::
    :::column:::
        FORMAT
    :::column-end:::
    :::column:::
        TEXTPTR
    :::column-end:::
:::row-end:::
 
## <a name="calling-extended-stored-procedures-from-functions"></a>Appel de procédures stockées étendues à partir de fonctions  
 Les fonctions qui appellent des procédures stockées étendues sont non déterministes car les procédures stockées étendues peuvent provoquer des effets secondaires sur la base de données. Ces effets secondaires sont des modifications de l'état global de la base de données, comme la mise à jour d'une table ou d'une ressource externe, telle qu'un fichier ou le réseau (par exemple la modification d'un fichier ou l'envoi d'un courrier électronique). N’attendez pas de jeu de résultats cohérent lors de l’exécution d’une procédure stockée étendue à partir d’une fonction définie par l’utilisateur. Les fonctions définies par l'utilisateur qui créent des effets secondaires sur la base de données ne sont pas recommandées.  
  
 Une procédure stockée étendue appelée depuis l'intérieur d'une fonction ne peut pas retourner de jeux de résultats au client. Toute API Open Data Services qui retourne des jeux de résultats au client a un code de retour FAIL.  
  
 La procédure stockée étendue ne peut pas se reconnecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cependant, la procédure ne peut pas joindre la même transaction que la fonction originale ayant appelé la procédure stockée étendue.  
  
 Comme pour les appels à partir d'une procédure stockée ou de traitement par lot, la procédure stockée étendue est exécutée dans le contexte du compte de sécurité [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel fonctionne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le propriétaire de la procédure stockée étendue doit prendre en compte les autorisations de ce contexte de sécurité quand il accorde à d’autres utilisateurs l’autorisation d’exécuter la procédure.  
  
  
