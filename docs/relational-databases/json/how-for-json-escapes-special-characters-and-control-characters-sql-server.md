---
title: "Comment FOR JSON place dans une séquence d’échappement les caractères spéciaux et les caractères de contrôle (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 0b0816ec492422b72abd22f0b493c6fc1670471a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Comment FOR JSON place dans une séquence d’échappement les caractères spéciaux et les caractères de contrôle (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cette rubrique explique comment la clause **FOR JSON** d’une instruction SQL Server **SELECT** place dans une séquence d’échappement les caractères spéciaux et représente les caractères de contrôle dans la sortie JSON.  

> [!IMPORTANT]
> Cette page décrit la prise en charge intégrée de JSON dans Microsoft SQL Server. Si vous souhaitez des informations générales sur l’échappement et l’encodage dans JSON, consultez la section 2.5 de la RFC JSON - [http://www.ietf.org/rfc/rfc4627.txt](http://www.ietf.org/rfc/rfc4627.txt).

## <a name="escaping-of-special-characters"></a>Échappement des caractères spéciaux  
Si les données sources contiennent des caractères spéciaux, la clause **FOR JSON** place ces caractères dans une séquence d’échappement dans la sortie JSON avec `\`, comme indiqué dans le tableau suivant. Cette opération se produit pour les noms des propriétés et leurs valeurs.  
  
|**Caractère spécial**|**Sortie placée dans une séquence d’échappement**|  
|---------------------------|--------------------------|  
|guillemets (")|\\"|  
|Barre oblique inverse (\\)|\\\|  
|Barre oblique (/)|\\/|  
|Retour arrière|\b|  
|Saut de page|\f|  
|Nouvelle ligne|\n|  
|Retour chariot|\r|  
|Tabulation horizontale|\t|  
  
## <a name="control-characters"></a>Caractères de contrôle  
Si les données sources contiennent des caractères de contrôle, la clause **FOR JSON** les encode dans la sortie JSON au format `\u<code>`, comme indiqué dans le tableau suivant.  
  
|**Caractère de contrôle**|**Sortie encodée**|  
|---------------------------|--------------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|…|…|  
|CHAR(31)|\u001f|  
  
## <a name="example"></a>Exemple  
 Voici un exemple de sortie **FOR JSON** pour des données sources contenant des caractères spéciaux et des caractères de contrôle.  
  
 Requête :  
  
```sql  
SELECT  
  'VALUE\    /  
  "' as [KEY\/"],  
  CHAR(0) as '0',  
  CHAR(1) as '1',  
  CHAR(31) as '31'  
FOR JSON PATH  
```  
  
 Résultat :  
  
```json  
{
    "KEY\\\t\/\"": "VALUE\\\t\/\r\n\"",
    "0": "\u0000",
    "1": "\u0001",
    "31": "\u001f"
}
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>En savoir plus sur la fonction intégrée prise en charge de JSON dans SQL Server  
Pour un grand nombre de solutions spécifiques, utilisez des cas et des recommandations, consultez le [billets de blog sur la prise en charge intégrée de JSON](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) dans SQL Server et dans la base de données SQL Azure par programme Jovan Popovic Gestionnaire Microsoft.
  
## <a name="see-also"></a>Voir aussi  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Clause FOR](../../t-sql/queries/select-for-clause-transact-sql.md)

