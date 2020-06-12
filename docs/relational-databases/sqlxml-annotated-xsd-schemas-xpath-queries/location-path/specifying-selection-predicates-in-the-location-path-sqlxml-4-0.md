---
title: Définir des prédicats de sélection dans le chemin d’accès d’emplacement (SQLXML)
description: Découvrez comment la spécification de prédicats de sélection dans l’expression de chemin d’emplacement d’une requête XPath (SQLXML 4,0) filtre l’ensemble de nœuds interrogé.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e3f62aa328573011d61a4a650aeb117516c3f9a6
ms.sourcegitcommit: 6593b3b6365283bb76c31102743cdccc175622fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84306195"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>Spécification de prédicats de sélection dans le chemin d'accès d'emplacement (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un prédicat filtre un élément node-set par rapport à un axe (semblable à une clause WHERE dans une instruction SELECT). Le prédicat est spécifié entre crochets. Pour chaque nœud de l'élément node-set à filtrer, l'expression de prédicat est évaluée avec ce nœud en tant que nœud de contexte et avec le nombre de nœuds de l'élément node-set en tant que taille de contexte. Si l'expression de prédicat prend la valeur TRUE pour ce nœud, ce dernier est inclus dans l'élément node-set obtenu.  
  
 XPath autorise également un filtrage basé sur les positions. Une expression de prédicat qui correspond à un nombre sélectionne ce nœud ordinal. Par exemple, le chemin d'accès d'emplacement `Customer[3]` retourne le troisième client. De tels prédicats numériques ne sont pas pris en charge. Seules les expressions de prédicat qui retournent un résultat booléen sont prises en charge.  
  
> [!NOTE]  
>  Pour plus d’informations sur les limitations de cette implémentation XPath de XPath et sur les différences entre elle et la spécification W3C, consultez [Introduction à l’utilisation de requêtes xpath &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="selection-predicate-example-1"></a>Prédicat de sélection : exemple 1  
 L’expression XPath suivante (chemin d’accès d’emplacement) sélectionne à partir du nœud de contexte actuel tous les **\<Customer>** éléments enfants dont l’attribut **CustomerID** a la valeur ALFKI :  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 Dans cette requête XPath, `child` et `attribute` sont les noms d'axes. `Customer`est le test de nœud (TRUE si `Customer` est un **\<element node>** , car **\<element>** est le type de nœud principal de l' `child` axe). `attribute::CustomerID="ALFKI"` est le prédicat. Dans le prédicat, `attribute` est l’axe et `CustomerID` est le test de nœud (true si **CustomerID** est un attribut du nœud de contexte, car **\<attribute>** est le type de nœud principal de l’axe d' **attribut** ).  
  
 À l'aide de la syntaxe abrégée, la requête XPath peut également être spécifiée de la façon suivante :  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>Prédicat de sélection : exemple 2  
 L’expression XPath suivante (chemin d’accès d’emplacement) sélectionne à partir du nœud de contexte actuel tous les petits-enfants ayant l' **\<Order>** attribut **SalesOrderID** avec la valeur 1 :  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 Dans cette expression XPath, `child` et `attribute` sont les noms des axes. `Customer`, `Order` et `SalesOrderID` sont les tests de nœud. `attribute::OrderID="1"` est le prédicat.  
  
 À l'aide de la syntaxe abrégée, la requête XPath peut également être spécifiée de la façon suivante :  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>Prédicat de sélection : exemple 3  
 L’expression XPath suivante (chemin d’accès d’emplacement) sélectionne à partir du nœud de contexte actuel tous les **\<Customer>** enfants qui ont un ou plusieurs **\<ContactName>** enfants :  
  
```  
child::Customer[child::ContactName]  
```  
  
 Cet exemple suppose que **\<ContactName>** est un élément enfant de l' **\<Customer>** élément dans le document XML, appelé *mappage centré* sur l’élément dans un schéma XSD annoté.  
  
 Dans cette expression XPath, `child` est le nom de l'axe. `Customer`est le test de nœud (TRUE si `Customer` est un **\<element>** nœud, car **\<element>** est le type de nœud principal pour `child` Axis). `child::ContactName` est le prédicat. Dans le prédicat, `child` est l’axe et `ContactName` est le test de nœud (true si `ContactName` est un **\<element>** nœud).  
  
 Cette expression retourne uniquement les **\<Customer>** éléments enfants du nœud de contexte qui ont des **\<ContactName>** éléments enfants.  
  
 À l'aide de la syntaxe abrégée, la requête XPath peut également être spécifiée de la façon suivante :  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>Prédicat de sélection : exemple 4  
 L’expression XPath suivante sélectionne les **\<Customer>** éléments enfants du nœud de contexte qui n’ont pas d' **\<ContactName>** éléments enfants :  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 Cet exemple suppose que **\<ContactName>** est un élément enfant de l' **\<Customer>** élément dans le document XML et que le champ ContactName n’est pas requis dans la base de données.  
  
 Dans cet exemple, `child` est l'axe. `Customer`est le test de nœud (TRUE si `Customer` est un \<element> nœud). `not(child::ContactName)` est le prédicat. Dans le prédicat, `child` est l’axe et `ContactName` est le test de nœud (true si `ContactName` est un \<element> nœud).  
  
 À l'aide de la syntaxe abrégée, la requête XPath peut également être spécifiée de la façon suivante :  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>Prédicat de sélection : exemple 5  
 L’expression XPath suivante sélectionne à partir du nœud de contexte actuel tous les **\<Customer>** enfants qui ont l’attribut **CustomerID** :  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 Dans cet exemple, `child` est l’axe et `Customer` est le test de nœud (true si `Customer` est un \<element> nœud). `attribute::CustomerID` est le prédicat. Dans le prédicat, `attribute` est l’axe et `CustomerID` est le PRÉDICAT (true si `CustomerID` est un **\<attribute>** nœud).  
  
 À l'aide de la syntaxe abrégée, la requête XPath peut également être spécifiée de la façon suivante :  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>Prédicat de sélection : exemple 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 inclut la prise en charge des requêtes XPath qui contiennent un produit croisé dans le prédicat, comme l'illustre l'exemple suivant :  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 Cette requête sélectionne tous les clients avec un `Order` quelconque pour lequel `OrderDate` est égal au `ShipDate` de tout `Order`.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des schémas XSD annotés &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [Mise en forme XML côté client &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
