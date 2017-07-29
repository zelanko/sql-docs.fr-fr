---
title: "Conversion par FOR JSON des types de données SQL Server en types de données JSON (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 527cb99c5caf0bb805e17f3b77b7d5e017e28ace
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

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
|Types CLR|Geometry, geography, autres types CLR|Non pris en charge. Ces types renvoient une erreur.<br /><br /> Dans l’instruction SELECT, utilisez CAST ou CONVERT, ou utiliser une propriété CLR ou une méthode pour convertir la source de données en un type de données SQL Server qui peut être converti correctement en type JSON. Par exemple, utilisez **STAsText()** pour le type geometry, ou utilisez **ToString()** pour n’importe quel type CLR. Le type de la valeur de sortie JSON est ensuite dérivé le type de retour de la conversion que vous appliquez dans l’instruction SELECT.|  
|Autres types|uniqueidentifier, money|chaîne|  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la fonction intégrée prise en charge de JSON dans SQL Server  
Pour un grand nombre de solutions spécifiques, utilisez des cas et des recommandations, consultez le [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et dans la base de données SQL Azure par programme Jovan Popovic Gestionnaire Microsoft.
  
## <a name="see-also"></a>Voir aussi  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  

