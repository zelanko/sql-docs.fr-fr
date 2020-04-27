---
title: Mise en forme XML côté client et côté serveur (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4eaa4667db1e8b6ed789e2adb90bc8d72c1b02e6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66012347"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a>Côté client et Mise en forme XML côté serveur (SQLXML 4.0)
  Cette rubrique décrit les principales différences entre la mise en forme XML côté client et côté serveur dans SQLXML.  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a>Les requêtes générant plusieurs ensembles de lignes ne sont pas prises en charge dans la mise en forme côté client  
 Les requêtes qui génèrent plusieurs ensembles de lignes ne sont pas prises en charge lorsque vous utilisez la mise en forme XML côté client. Supposons par exemple que vous ayez un répertoire virtuel dans lequel une mise en forme côté client est spécifiée. Considérez cet exemple de modèle, qui contient deux instructions SELECT dans un ** \<bloc de>SQL : Query** :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 Si vous exécutez ce modèle dans un code d'application, une erreur est alors retournée car la mise en forme XML côté client ne prend pas en charge la mise en forme de plusieurs ensembles de lignes. Si vous spécifiez les requêtes dans deux blocs ** \<SQL : Query>** distincts, vous obtiendrez les résultats souhaités.  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a>timestamp est mappé différemment dans la mise en forme côté client et la mise en forme côté serveur  
 Dans la mise en forme XML côté serveur, la colonne de base de données de type `timestamp` est mappée au type XDR i8 (lorsque l'option XMLDATA est spécifiée dans la requête).  
  
 Dans la mise en forme XML côté client, la colonne de base de données de type `timestamp` est mappée au type XDR `uri` ou `bin.base64` (selon que l'option BINARY BASE64 est spécifiée dans la requête). Le `bin.base64` type XDR est utile si vous utilisez les fonctionnalités mise à jour et bulkload, car ce type est converti en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` type. De cette manière, l'opération insert, update ou delete réussit.  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a>Les sous-types Deep du type VARIANT sont utilisés dans la mise en forme côté serveur  
 Dans la mise en forme XML côté serveur, les types Deep d'un type de données VARIANT sont utilisés. Si vous utilisez la mise en forme XML côté client, les variantes sont converties en chaîne Unicode et les sous-types de VARIANT ne sont pas utilisés.  
  
## <a name="nested-mode-vs-auto-mode"></a>Mode NESTED et mode AUTO  
 Le mode NESTED de FOR XML côté client est semblable au mode AUTO de FOR XML côté serveur, avec les exceptions suivantes :  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a>Lorsque vous interrogez des vues à l'aide du mode AUTO côté serveur, le nom de la vue est retourné comme nom de l'élément dans le XML résultant.  
 Par exemple, supposons que la vue suivante est créée sur la table Person. contact dans AdventureWorksdatabase :  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 Le modèle suivant spécifie une requête sur la vue ContactView, de même que la mise en forme XML côté serveur :  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Lorsque vous exécutez le modèle, le XML suivant est retourné (Seuls les résultats partiels sont affichés.) Notez que les noms d’éléments sont les noms des vues sur lesquelles la requête est exécutée.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 Lorsque vous spécifiez la mise en forme XML côté client en utilisant le mode NESTED correspondant, les noms des tables de base sont retournés comme noms des éléments dans le XML résultant. Par exemple, le modèle modifié suivant exécute la même instruction SELECT, mais la mise en forme XML est effectuée côté client (autrement dit, le **code XML côté client** est défini sur true dans le modèle) :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 L'exécution de ce modèle génère le XML suivant. Notez que dans ce cas, le nom de l'élément correspond au nom de la table de base.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a>Lorsque vous utilisez le mode AUTO de FOR XML côté serveur, les alias de tables spécifiés dans la requête sont retournés en tant que noms des éléments dans le XML résultant.  
 Considérons par exemple le modèle suivant :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 L'exécution de ce modèle génère le XML suivant :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 Lorsque vous utilisez le mode NESTED de FOR XML côté client, les noms des tables sont retournés en tant que noms des éléments dans le XML résultant. (Les alias de tables spécifiés dans la requête ne sont pas utilisés.) Par exemple, considérez ce modèle :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 L'exécution de ce modèle génère le XML suivant :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a>Si une requête retourne des colonnes sous forme de requêtes dbobject, vous ne pouvez pas utiliser d'alias pour ces colonnes.  
 Considérons par exemple le modèle suivant qui exécute une requête retournant un ID d'employé et une photo.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 L'exécution de ce modèle retourne la colonne Photo sous forme de requête dbobject. Dans cette requête dbobject, `@P` fait référence à un nom de colonne qui n'existe pas.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 Si la mise en forme XML est effectuée sur le serveur (**client-side-xml = "0"**), vous pouvez utiliser l’alias pour les colonnes qui retournent des requêtes DBOBJECT dans lesquelles les noms de tables et de colonnes réels sont retournés (même si vous avez spécifié des alias). Par exemple, le modèle suivant exécute une requête, et la mise en forme XML est effectuée sur le serveur (l’option **Client-Side-XML** n’est pas spécifiée et l’option **exécuter sur le client** n’est pas sélectionnée pour la racine virtuelle). La requête spécifie également le mode AUTO (pas le mode NESTED côté client).  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 Lorsque ce modèle est exécuté, le document XML suivant est retourné (notez que les alias ne sont pas utilisés dans la requête dbobject pour la colonne LargePhoto) :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a>XPath côté client et côté serveur  
 XPath côté client et XPath côté serveur fonctionnement de la même manière, à quelques différences près :  
  
-   Les conversions de données appliquées lorsque vous utilisez des requêtes XPath côté client sont différentes de celles qui s'appliquent lorsque vous utilisez des requêtes XPath côté serveur. Les requêtes XPath côté client utilisent CAST au lieu du mode CONVERT 126.  
  
-   Lorsque vous spécifiez **client-side-xml = "0"** (false) dans un modèle, vous demandez une mise en forme XML côté serveur. Par conséquent, vous ne pouvez pas spécifier FOR XML NESTED car le serveur ne reconnaît pas l'option NESTED. Cela génère une erreur. Vous devez utiliser les modes AUTO, RAW ou EXPLICIT, que le serveur reconnaît.  
  
-   Lorsque vous spécifiez **client-side-xml = "1"** (true) dans un modèle, vous demandez la mise en forme XML côté client. Dans ce cas, vous pouvez spécifier FOR XML NESTED. Si vous spécifiez FOR XML AUTO, la mise en forme XML se produit côté serveur, bien que le **client-side-xml = "1"** soit spécifié dans le modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations relatives à la sécurité XML &#40;SQLXML 4,0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [Mise en forme XML côté client &#40;SQLXML 4,0&#41;](client-side-xml-formatting-sqlxml-4-0.md)   
 [La mise en forme XML côté serveur &#40;SQLXML 4,0&#41;](server-side-xml-formatting-sqlxml-4-0.md)  
  
  
