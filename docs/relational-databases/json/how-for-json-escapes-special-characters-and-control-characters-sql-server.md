---
title: "Comment FOR JSON place dans une s&#233;quence d’&#233;chappement les caract&#232;res sp&#233;ciaux et les caract&#232;res de contr&#244;le (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON, caractères spéciaux"
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Comment FOR JSON place dans une s&#233;quence d’&#233;chappement les caract&#232;res sp&#233;ciaux et les caract&#232;res de contr&#244;le (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique explique comment la clause **FOR JSON** place dans une séquence d’échappement les caractères spéciaux et représente les caractères de contrôle dans la sortie JSON.  
  
## Échappement des caractères spéciaux  
 La clause **FOR JSON** place dans une séquence d’échappement les caractères spéciaux de la sortie JSON avec `\`, comme indiqué dans le tableau suivant. Cette opération se produit pour les noms des propriétés et leurs valeurs.  
  
|**Caractère spécial**|**Séquence codée**|  
|---------------------------|--------------------------|  
|guillemets (")|\\"|  
|Barre oblique inverse (\\)|\\\|  
|Barre oblique (/)|\\/|  
|Retour arrière|\b|  
|Saut de page|\f|  
|Nouvelle ligne|\n|  
|Retour chariot|\r|  
|Tabulation horizontale|\t|  
  
## Caractères de contrôle  
 La clause **FOR JSON** représente les caractères de contrôle dans la sortie JSON au format `\u<code>`, comme indiqué dans le tableau suivant.  
  
|**Caractère de contrôle**|**Séquence codée**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|…|…|  
|CHAR(31)|\u001f|  
  
## Exemple  
 Voici un exemple d’une clause **FOR JSON** qui inclut des caractères de contrôle et d’échappement.  
  
 Requête :  
  
```tsql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 Résultat :  
  
```json  
{  
   "KEY\\\t\/\"":"VALUE\\\t\/\r\n\"",  
   "0":"\u0000",  
   "1":"\u0001",  
  "31":"\u001f“  
}  
```  
  
## Voir aussi  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  