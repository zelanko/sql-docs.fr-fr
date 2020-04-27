---
title: Spécification d’opérateurs booléens dans les requêtes XPath (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29404c4a3dc7b4b10106e7a3a8cb170ffe1e7a3e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010632"
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a>Spécification d'opérateurs booléens dans les requêtes XPath (SQLXML 4.0)
  L'exemple suivant montre comment les opérateurs booléens sont spécifiés dans les requêtes XPath. La requête XPath de cet exemple est spécifiée par rapport au schéma de mappage contenu dans SampleSchema1.xml. Pour plus d’informations sur cet exemple de schéma, consultez [exemple de schéma XSD annoté pour les exemples XPath &#40;SQLXML 4,0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-specify-the-or-boolean-operator"></a>R. Spécifier l'opérateur booléen OR  
 Cette requête XPath retourne le ** \<client>** éléments enfants du nœud de contexte avec la valeur d’attribut **CustomerID** 13 ou 31 :  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 Il est possible de spécifier un raccourci vers l'axe `attribute` (@), et l'axe `child` étant l'axe par défaut, il peut être omis :  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 Dans le prédicat `attribute` , est l’axe et `CustomerID` est le test de nœud (true si **CustomerID** est un ** \<attribut>** nœud, car l' ** \<attribut>** nœud est le nœud principal de l' `attribute` axe). Le prédicat filtre les éléments du ** \<>client** et retourne uniquement ceux qui répondent à la condition spécifiée dans le prédicat.  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a>Pour tester les requêtes XPath par rapport au schéma de mappage  
  
1.  Copiez l' [exemple de code de schéma](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom SampleSchema1.xml.  
  
2.  Créez le modèle ci-après (BooleanOperatorsA.xml) et enregistrez-le dans le même répertoire que SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleSchema1.xml) varie en fonction du répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats de l'exécution du modèle :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
