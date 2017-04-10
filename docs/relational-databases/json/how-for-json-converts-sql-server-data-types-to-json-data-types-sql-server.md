---
title: "Conversion par FOR JSON des types de donn&#233;es SQL&#160;Server en types de donn&#233;es JSON (SQL&#160;Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON, conversion de types de données"
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# Conversion par FOR JSON des types de donn&#233;es SQL&#160;Server en types de donn&#233;es JSON (SQL&#160;Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  La clause **FOR JSON** utilise les règles ci-après pour convertir les types de données SQL Server en types JSON dans la sortie JSON.  
  
|Catégorie|Type de données SQL Server|Type de données JSON|  
|--------------|--------------|---------------|  
|Types caractères et chaînes|(n)(var)(char)|chaîne|  
|Types valeurs numériques|int, bigint, float, decimal, numeric|nombre|  
|Types bits|bit|Booléen (true ou false)|  
|Types dates et heures|date, datetime, datetime2, time, datetimeoffset|chaîne|  
|Types données binaires|varbinary, binary, image, timestamp, rowversion|Chaîne codée en Base64|  
|Types CLR|CLR, geometry, geography|Non pris en charge. Ces types renvoient une erreur.<br /><br /> Dans l’instruction SELECT, utilisez CAST ou CONVERT, ou bien une méthode ou une propriété CLR, pour convertir les données en un type de données pouvant être converti en type JSON. Par exemple, utilisez **ToString()** pour n’importe quel type CLR, ou **STAsText()** pour le type geometry. Le type de la valeur de sortie JSON est ensuite dérivé du type de retour de la conversion que vous utilisez dans l’instruction SELECT.|  
|Autres types|uniqueidentifier, money|chaîne|  
  
## Voir aussi  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  