---
title: Comment FOR JSON place dans une séquence d’échappement les caractères spéciaux et les caractères de contrôle (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: genemi
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON, special characters
ms.assetid: 4ba90025-5a09-4f0a-836a-54c886324530
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 508a50443e039fa77f1190c5a00b6ffdbf93379a
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70910814"
---
# <a name="how-for-json-escapes-special-characters-and-control-characters-sql-server"></a>Comment FOR JSON place dans une séquence d’échappement les caractères spéciaux et les caractères de contrôle (SQL Server)

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Cette rubrique explique comment la clause **FOR JSON** d’une instruction SQL Server **SELECT** place dans une séquence d’échappement les caractères spéciaux et représente les caractères de contrôle dans la sortie JSON.  

> [!IMPORTANT]
> Cette page décrit la prise en charge intégrée de JSON dans Microsoft SQL Server. Si vous souhaitez des informations générales sur l’échappement et l’encodage dans JSON, consultez la section 2.5 de la RFC JSON - [https://www.ietf.org/rfc/rfc4627.txt](https://www.ietf.org/rfc/rfc4627.txt).

## <a name="escaping-of-special-characters"></a>Échappement des caractères spéciaux  
Si les données sources contiennent des caractères spéciaux, la clause **FOR JSON** place ces caractères dans une séquence d’échappement dans la sortie JSON avec `\`, comme indiqué dans le tableau suivant. Cette opération se produit pour les noms des propriétés et leurs valeurs.  
  
|**Caractère spécial**|**Sortie placée dans une séquence d’échappement**|  
|---------------------------|--------------------------|  
|guillemets (")|\\"|  
|Barre oblique inverse (\\)|\\\\|  
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
|...|...|  
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

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>En savoir plus sur JSON dans SQL Server et Azure SQL Database  
  
### <a name="microsoft-videos"></a>Vidéos Microsoft

Pour obtenir une présentation visuelle de la prise en charge intégrée de JSON dans SQL Server et Azure SQL Database, consultez les vidéos suivantes :

-   [SQL Server 2016 et prise en charge de JSON](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Utilisation de JSON dans SQL Server 2016 et Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON : un pont entre les mondes relationnel et NoSQL](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)
  
## <a name="see-also"></a>Voir aussi  
 [Mettre les résultats de requête au format JSON avec FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
[Clause FOR](../../t-sql/queries/select-for-clause-transact-sql.md)
