---
title: Définir la sérialisation des données XML | Microsoft Docs
description: En savoir plus sur les règles utilisées lors de la sérialisation de données xml dans SQL Server.
ms.custom: ''
ms.date: 12/07/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- entitization rules [XML in SQL Server]
- serialization
- reparsing serialized XML structures
- encoding [XML in SQL Server]
- XML [SQL Server], serialization
- xml data type [SQL Server], serialization
- typed XML
ms.assetid: 42b0b5a4-bdd6-4a60-b451-c87f14758d4b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 67201804cc1f93a9595ff46c02a57da7ea6e6109
ms.sourcegitcommit: 68063a1857f40487e6a2028de25990728419e3a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96749701"
---
# <a name="define-the-serialization-of-xml-data"></a>Définir la sérialisation des données XML
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Lors de la conversion explicite ou implicite du type de données xml en données SQL de type chaîne ou binaire, le contenu des données de type xml sera sérialisé conformément aux règles présentées dans cette rubrique.  
  
## <a name="serialization-encoding"></a>Encodage de la sérialisation  
 Si le type cible SQL est VARBINARY, le résultat est sérialisé au format UTF-16 avec une marque d'ordre d'octet UTF-16 au début, mais sans déclaration XML. Si le type cible est trop petit, une erreur est générée.  
  
 Par exemple :  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARBINARY(MAX))  
```  
  
 Voici le résultat obtenu :  
  
```console
0xFFFE3C0094032F003E00  
```  
  
 Si le type cible SQL est NVARCHAR ou NCHAR, le résultat est sérialisé au format UTF-16 sans marque d'ordre d'octet au début ni déclaration XML. Si le type cible est trop petit, une erreur est générée.  
  
 Par exemple :  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as NVARCHAR(MAX))  
```  
  
 Voici le résultat obtenu :  
  
```console
<Δ/>  
```  
  
 Si le type cible SQL est VARCHAR ou CHAR, le résultat est sérialisé dans l’encodage correspondant à la page de codes du classement de la base de données sans marque d’ordre d’octet ni déclaration XML. Si le type cible est trop petit ou s'il est impossible de faire correspondre la valeur à la page de codes du classement de la cible, une erreur est générée.  
  
 Par exemple :  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARCHAR(MAX))  
```  
  
 Une erreur peut se produire si la page de codes du classement actuel ne peut pas représenter le caractère Unicode Δ, sinon l'encodage spécifique sera utilisé.  
  
 Lors du renvoi des résultats XML côté client, les données seront transmises en UTF-16. Le fournisseur côté client exposera ensuite les données d'après les règles de son API.  
  
## <a name="serialization-of-the-xml-structures"></a>Sérialisation des structures XML  
 Le contenu d’un type de données **xml** est sérialisé de manière habituelle. Plus précisément, les nœuds d'élément sont mappés au balisage d'élément et les nœuds de texte sont mappés au contenu texte. Les circonstances dans lesquelles les caractères sont décomposés en entités et la façon dont les valeurs atomiques typées sont sérialisées sont décrites dans les sections suivantes.  
  
## <a name="entitization-of-xml-characters-during-serialization"></a>Codage d'entité des caractères XML au cours de la sérialisation  
 Chaque structure XML sérialisée doit pouvoir subir une nouvelle analyse. C’est pourquoi certains caractères doivent être sérialisés à l’aide du codage d’entité de façon à autoriser les accès répétés aux caractères, tout au long de la phase de normalisation de l’analyseur XML. Il s'avère aussi nécessaire de spécifier le codage d'entité de certains caractères afin d'assurer la bonne formation du document et son analyse. Voici les règles de codage d'entité qui s'appliquent au cours de la sérialisation :  
  
-   Les caractères &, \<, and > sont toujours codés sous la forme `&amp;`, `&lt;` et `&gt;`, respectivement, s’ils se trouvent dans la valeur d’un attribut ou dans le contenu d’un élément.  
  
-   Étant donné que SQL Server utilise les guillemets (U+0022) pour délimiter les valeurs des attributs, le guillemet des valeurs de l’attribut est codé par `&quot;`.  
  
-   Une paire de substitution est codée sous forme d'une seule référence de caractère numérique, lors de la conversion sur le serveur uniquement. Par exemple, la paire de substitution U+D800 U+DF00 est codée par la référence de caractère numérique `&#x00010300;`.  
  
-   Pour empêcher leur normalisation lors de l’analyse, la tabulation (U+0009) et le saut de ligne (LF, U+000A) sont codés par leur référence de caractère numérique, respectivement `&#x9;` et `&#xA;`, dans les valeurs d’attribut.  
  
-   Pour empêcher sa normalisation lors de l’analyse, le retour chariot (CR, U+000D) est codé par sa référence de caractère numérique, `&#xD;` dans les valeurs d’attribut et le contenu des éléments.  
  
-   Pour protéger les nœuds de texte contenant des espaces, l'un des espaces (généralement le dernier) est codé par sa référence de caractère numérique. De cette façon, l'analyse préserve le nœud de texte contenant des espaces, quel que soit le mode de traitement choisi pour les espaces au cours de l'analyse.  
  
 Par exemple :  
  
```sql
declare @u NVARCHAR(50)  
set @u = N'<a a="  
    '+NCHAR(0xD800)+NCHAR(0xDF00)+N'>">   '+NCHAR(0xA)+N'</a>'  
select CAST(CONVERT(XML,@u,1) as NVARCHAR(50))  
```  
  
 Voici le résultat obtenu :  
  
```console
<a a="  
    𐌀>">     
</a>  
```  
  
 Si vous ne voulez pas appliquer la règle de protection du dernier espace, vous pouvez utiliser explicitement l’option 1 de CONVERT lors de la conversion de **xml** en type chaîne ou binaire. Par exemple, vous pouvez éviter le codage d'entité en procédant ainsi :  
  
```sql
select CONVERT(NVARCHAR(50), CONVERT(XML, '<a>   </a>', 1), 1)  
```  
  
 Remarquez que la [méthode query() (type de données xml)](../../t-sql/xml/query-method-xml-data-type.md) génère une instance de type xml. Ainsi, tout résultat de la méthode **query()** converti en type chaîne ou binaire a recours au codage d’entité conformément aux règles précédemment décrites. Si vous souhaitez obtenir les valeurs de chaîne sans conversion en entité, utilisez la [méthode value() (type de données xml)](../../t-sql/xml/value-method-xml-data-type.md) . L’exemple suivant montre comment utiliser la méthode **query()** :  
  
```sql
declare @x xml  
set @x = N'<a>This example contains an entitized char: <.</a>'  
select @x.query('/a/text()')  
```  
  
 Voici le résultat obtenu :  
  
```console
This example contains an entitized char: <.  
```  
  
 L’exemple suivant montre comment utiliser la méthode **value()** :  
  
```sql
select @x.value('(/a/text())[1]', 'nvarchar(100)')  
```  
  
 Voici le résultat obtenu :  
  
```console
This example contains an entitized char: <.  
```  
  
## <a name="serializing-a-typed-xml-data-type"></a>Sérialisation de données typées XML  
 Une instance typée **xml** contient des valeurs qui sont typées en fonction de leurs types de schémas XML. Ces valeurs sont sérialisées selon leur type de schéma XML au format que produit la conversion XQuery vers xs:string. Pour plus d’informations, consultez [Règles de conversion de types dans XQuery](../../xquery/type-casting-rules-in-xquery.md).  
  
 Par exemple, la valeur xs:double 1.34e1 est sérialisée en 13.4 comme le montre l'exemple suivant :  
  
```sql
declare @x xml  
set @x =''  
select CAST(@x.query('1.34e1') as nvarchar(50))  
```  
  
 Cela renvoie la valeur de chaîne 13.4.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conversion de types dans XQuery](../../xquery/type-casting-rules-in-xquery.md)   
 [CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
 
