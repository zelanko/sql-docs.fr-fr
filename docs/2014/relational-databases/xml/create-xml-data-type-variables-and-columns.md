---
title: Créer des variables et des colonnes de type de données XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- xml data type [SQL Server], columns
ms.assetid: 8994ab6e-5519-4ba2-97a1-fac8af6f72db
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1ee22addfb4d7a4b8162a1cd57ca51120c8acc47
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889435"
---
# <a name="create-xml-data-type-variables-and-columns"></a>Créer des variables et des colonnes de type de données XML
  Le type de données `xml` est un type de données intégré à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], quelque peu similaire aux autres types intégrés, tels que `int` et `varchar`. Comme avec d’autres types intégrés, vous pouvez utiliser la `xml` de type de données comme type de colonne lorsque vous créez une table sous la forme d’un type de variable, un type de paramètre, un type de retour de fonction, ou dans [CAST et CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
## <a name="creating-columns-and-variables"></a>Création de variables et de colonnes  
 Pour créer une colonne de type `xml` dans le cadre d’une table, utilisez une instruction `CREATE TABLE` , comme illustré dans l’exemple suivant :  
  
```  
CREATE TABLE T1(Col1 int primary key, Col2 xml)   
```  
  
 Vous pouvez utiliser une `DECLARE statement` pour créer une variable de type `xml` , comme le montre l’exemple suivant.  
  
```  
DECLARE @x xml   
```  
  
 Créez une variable `xml` typée en spécifiant une collection de schémas XML, comme illustré dans l'exemple suivant.  
  
```  
DECLARE @x xml (Sales.StoreSurveySchemaCollection)  
```  
  
 Pour passer un paramètre de type `xml` à une procédure stockée, utilisez une instruction `CREATE PROCEDURE` , comme illustré dans l’exemple suivant.  
  
```  
CREATE PROCEDURE SampleProc(@XmlDoc xml) AS ...   
```  
  
 Vous pouvez utiliser XQuery pour interroger des instances XML stockées dans des colonnes, paramètres ou variables. Vous pouvez également utiliser le langage de manipulation de données XML pour appliquer des mises à jour aux instances XML. Le développement du standard XQuery n’ayant pas donné lieu à la définition d’une syntaxe DML XQuery, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] introduit des extensions [DML XML (XML Data Modification Language)](/sql/t-sql/xml/xml-data-modification-language-xml-dml) dans XQuery. Ces extensions vous permettent de réaliser des opérations d'insertion, de mise à jour et de suppression.  
  
## <a name="assigning-defaults"></a>Affectation de valeurs par défaut  
 Dans une table, vous pouvez affecter une instance XML par défaut à une colonne de type `xml`. Vous pouvez fournir le XML par défaut de deux manières : en utilisant une constante XML ou en utilisant un cast explicite au type `xml`.  
  
 Pour fournir le XML par défaut en tant que constante XML, utilisez la syntaxe comme illustré dans l'exemple suivant. Notez que la chaîne est convertie implicitement au `xml` type.  
  
```  
CREATE TABLE T (XmlColumn xml default N'<element1/><element2/>')  
```  
  
 Pour fournir le XML par défaut en tant que `CAST` explicite au type `xml`, utilisez la syntaxe comme illustré dans l'exemple suivant.  
  
```  
CREATE TABLE T (XmlColumn xml   
                  default CAST(N'<element1/><element2/>' AS xml))  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend également en charge les contraintes NULL et NOT NULL sur des colonnes de type `xml`. Exemple :  
  
```  
CREATE TABLE T (XmlColumn xml NOT NULL)  
```  
  
## <a name="specifying-constraints"></a>Spécification de contraintes  
 Lorsque vous créez des colonnes de type `xml`, vous pouvez définir des contraintes de niveau colonne ou de niveau table. Utilisez les contraintes dans les cas suivants :  
  
-   Vos règles d'entreprise ne peuvent pas être exprimées dans les schémas XML. Par exemple, l'adresse de livraison d'un fleuriste doit se trouver à 80 km du magasin. Cela peut faire l'objet d'une contrainte dans la colonne XML. La contrainte peut impliquer des méthodes de type de données `xml`.  
  
-   Votre contrainte implique d'autres colonnes XML ou non XML de la table. Vous pourriez, par exemple, vouloir absolument que l'ID d'un client (`/Customer/@CustId`) figurant dans une instance XML corresponde à la valeur d'une colonne relationnelle CustomerID.  
  
 Vous pouvez spécifier des contraintes pour les colonnes de type de données `xml` typées ou non typées. Toutefois, vous ne pouvez pas utiliser les [méthodes de type de données xm](/sql/t-sql/xml/xml-data-type-methods) lorsque vous spécifiez des contraintes. Notez également que le type de données `xml` ne prend pas en charge les contraintes de colonne et de table suivantes :  
  
-   PRIMARY KEY/ FOREIGN KEY  
  
-   UNIQUE  
  
-   COLLATE  
  
     XML fournit son propre encodage. Les classements ne s'appliquent qu'aux types chaîne. Le type de données `xml` n'est pas un type chaîne. Toutefois, il possède une représentation chaîne et permet la conversion en provenance et en direction des types de données chaîne.  
  
-   RULE  
  
 Une alternative à l’aide de contraintes consiste à créer un wrapper, la fonction définie par l’utilisateur pour encapsuler le `xml` méthode de type de données et spécifier la fonction définie par l’utilisateur dans la contrainte de validation comme indiqué dans l’exemple suivant.  
  
 Dans l'exemple suivant, la contrainte sur `Col2` spécifie que chaque instance XML stockée dans cette colonne doit posséder un élément `<ProductDescription>` doté d'un attribut `ProductID` . Cette contrainte est appliquée par cette fonction définie par l'utilisateur :  
  
```  
CREATE FUNCTION my_udf(@var xml) returns bit  
AS BEGIN   
RETURN @var.exist('/ProductDescription/@ProductID')  
END  
GO  
```  
  
 La méthode `exist()` du type de données `xml` renvoie `1` si l'élément `<ProductDescription>` de l'instance contient l'attribut `ProductID` . Sinon, `0`est retourné.  
  
 Maintenant, vous pouvez créer une table dotée d'une contrainte de niveau colonne, comme suit :  
  
```  
CREATE TABLE T (  
    Col1 int primary key,   
    Col2 xml check(dbo.my_udf(Col2)=1))  
GO  
```  
  
 L'insertion suivante réussit :  
  
```  
INSERT INTO T values(1,'<ProductDescription ProductID="1" />')  
```  
  
 La contrainte fait échouer l'insertion suivante :  
  
```  
INSERT INTO T values(1,'<Product />')  
```  
  
## <a name="same-or-different-table"></a>Table identique ou différente  
 Un `xml` colonne de type de données peut être créée dans une table qui contient d’autres colonnes relationnelles ou dans une table distincte dotée d’une relation de clé étrangère avec une table principale.  
  
 Créer un `xml` colonne de type de données dans la même table lorsqu’une des conditions suivantes est vraie :  
  
-   Votre application récupère les données dans la colonne XML sans exiger qu'un index XML existe dans la colonne XML.  
  
-   Vous voulez créer un index XML sur la colonne de type `xml` et la clé primaire de la table principale est identique à sa clé de clustering. Pour plus d’informations, consultez [Index XML &#40;SQL Server&#41;](xml-indexes-sql-server.md).  
  
 Créer le `xml` colonne de type de données dans une table distincte si les conditions suivantes sont remplies :  
  
-   Vous souhaitez créer un index XML sur le `xml` colonne de type de données, mais la clé primaire de la table principale est différente de sa clé de clustering, ou de la table principale n’a pas une clé primaire ou de la table principale est un segment de mémoire (sans clé de clustering). Cela peut se produire si la table principale existe déjà.  
  
-   Vous ne voulez pas voir les analyses de la table ralentir suite à la présence d'une colonne XML dans la table. La quantité d'espace utilisée varie selon que le stockage se fait en ligne ou hors ligne.  
  
  
