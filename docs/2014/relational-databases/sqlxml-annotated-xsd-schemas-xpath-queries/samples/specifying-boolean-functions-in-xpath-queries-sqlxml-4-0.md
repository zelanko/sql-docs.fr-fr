---
title: Spécification de fonctions booléennes dans des requêtes XPath (SQLXML 4.0) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], Boolean functions
- false function
- not function [SQLXML]
- true function
- Boolean functions
ms.assetid: c72cd333-9294-4d41-84f2-1748bf20e3eb
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 06b35c5a8e2e7e6e03c0fd943572b25b30bf017e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044484"
---
# <a name="specifying-boolean-functions-in-xpath-queries-sqlxml-40"></a>Spécification de fonctions booléennes dans des requêtes XPath (SQLXML 4.0)
  Les exemples suivants montrent comment spécifier des fonctions booléennes dans des requêtes XPath. Les requêtes XPath de ces exemples sont spécifiées par rapport au schéma de mappage contenu dans SampleSchema1.xml. Pour plus d’informations sur cet exemple de schéma, consultez [exemple de schéma XSD annoté pour obtenir des exemples XPath &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Exemples  
  
## <a name="a-specify-the-not-boolean-function"></a>A. Spécifier la fonction booléenne not()  
 Cette requête retourne tous les  **\<client >** des éléments enfants du nœud de contexte qui n’ont pas  **\<ordre >** des éléments enfants :  
  
```  
/child::Customer[not(child::Order)]  
```  
  
 L'axe `child` est la valeur par défaut. Par conséquent, la requête peut être spécifiée sous la forme :  
  
```  
/Customer[not(Order)]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Pour tester la requête XPath par rapport au schéma de mappage  
  
1.  Copie le [exemple de code de schéma](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom SampleSchema1.xml.  
  
2.  Créez le modèle ci-dessous (BooleanFunctionsA.xml) et enregistrez-le dans le même répertoire que SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[not(Order)]  
    </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleSchema1.xml) varie en fonction du répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [à l’aide d’ADO pour exécuter des requêtes SQLXML 4.0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel de l'exécution du modèle :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
## <a name="b-specify-the-true-and-false-boolean-functions"></a>B. Spécifier les fonctions booléennes true() et false()  
 Cette requête retourne tous les  **\<client >** éléments enfants du nœud de contexte qui n’ont pas  **\<ordre >** des éléments enfants. En termes relationnels, cette requête retourne tous les clients qui n'ont pas passé de commandes.  
  
```  
/child::Customer[child::Order=false()]  
```  
  
 L'axe `child` est la valeur par défaut. Par conséquent, la requête peut être spécifiée sous la forme :  
  
```  
/Customer[Order=false()]  
```  
  
 Cette requête est équivalente à la suivante :  
  
```  
/Customer[not(Order)]  
```  
  
 La requête ci-dessous retourne tous les clients qui ont passé au moins une commande :  
  
```  
/Customer[Order=true()]  
```  
  
 Cette requête est équivalente à la requête suivante :  
  
```  
/Customer[Order]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Pour tester la requête XPath par rapport au schéma de mappage  
  
1.  Copie le [exemple de code de schéma](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom SampleSchema1.xml.  
  
2.  Créez le modèle ci-dessous (BooleanFunctionsB.xml) et enregistrez-le dans le même répertoire que SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order=false()]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleSchema1.xml) varie en fonction du répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [à l’aide d’ADO pour exécuter des requêtes SQLXML 4.0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel de l'exécution du modèle :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
  