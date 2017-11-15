---
title: "Conversion par FOR JSON des types de données SQL Server en types de données JSON (SQL Server) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 07/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b1744d9300d7a27087ebac6d7ef3f5dc00805750
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>Conversion par FOR JSON des types de données SQL Server en types de données JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  La clause **FOR JSON** utilise les règles ci-après pour convertir les types de données SQL Server en types JSON dans la sortie JSON.  
  
|Catégorie|Type de données SQL Server|Type de données JSON|  
|--------------|--------------|---------------|  
|Types caractères et chaînes|char, nchar, varchar, nvarchar|chaîne|  
|Types valeurs numériques|int, bigint, float, decimal, numeric|nombre|  
|Types bits|bit|Booléen (true ou false)|  
|Types dates et heures|date, datetime, datetime2, time, datetimeoffset|chaîne|  
|Types données binaires|varbinary, binary, image, timestamp, rowversion|Chaîne codée en Base64|  
|Types CLR|geometry, geography, autres types CLR|Non pris en charge. Ces types renvoient une erreur.<br /><br /> Dans l’instruction SELECT, utilisez CAST ou CONVERT, ou bien une propriété ou méthode CLR, pour convertir les données sources en type de données SQL Server pouvant être converti correctement en type JSON. Par exemple, utilisez **STAsText()** pour le type geometry, ou **ToString()** pour un type CLR. Le type de la valeur de sortie JSON est ensuite dérivé du type de retour de la conversion que vous appliquez dans l’instruction SELECT.|  
|Autres types|uniqueidentifier, money|chaîne|  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la prise en charge intégrée de JSON dans SQL Server  
Pour accéder à un grand nombre de solutions spécifiques, de cas d’usage et de recommandations, consultez les [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et Azure SQL Database, écrits par Jovan Popovic (Microsoft Program Manager).
  
## <a name="see-also"></a>Voir aussi  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  
