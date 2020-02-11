---
title: Générer des frères à l’aide d’une requête imbriquée en mode AUTO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- queries [XML in SQL Server], nested AUTO mode
- nested AUTO mode query
ms.assetid: 748d9899-589d-4420-8048-1258e9e67c20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0db2a84b4be80fffec0f05aed11f39a3bcea7db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63287360"
---
# <a name="generate-siblings-with-a-nested-auto-mode-query"></a>Générer des frères à l'aide d'une requête imbriquée en mode AUTO
  L'exemple suivant indique comment générer des frères à l'aide d'une requête imbriquée en mode AUTO. La seule autre façon de générer ce type de document XML consiste à utiliser le mode EXPLICIT. Toutefois, cette méthode peut s'avérer lourde.  
  
## <a name="example"></a>Exemple  
 Cette requête construit le document XML qui fournit les informations sur les commandes. Notamment :  
  
-   Les informations sur les en-têtes des commandes, `SalesOrderID`, `SalesPersonID`et `OrderDate`. [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] stocke ces informations dans la table `SalesOrderHeader` .  
  
-   Les informations sur les détails des commandes. Elles indiquent un ou plusieurs produits commandés, le prix unitaire et la quantité commandée. Ces informations sont stockées dans la table `SalesOrderDetail` .  
  
-   Les informations sur le vendeur. Il s'agit du vendeur qui a traité la commande. La table `SalesPerson` fournit le `SalesPersonID`. Pour cette requête, vous devez joindre cette table à la table `Employee` afin de rechercher le nom du vendeur.  
  
 Les deux requêtes `SELECT` distinctes ci-après génèrent un document XML dont la forme varie peu.  
  
 La première requête génère un document XML dans lequel <`SalesPerson`> et <`SalesOrderHeader`> apparaissent en tant qu'enfants frères de <`SalesOrder`> :  
  
```  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID =   
                   SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
        FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
        for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As   
                     SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
```  
  
 Dans la requête précédente, l'instruction `SELECT` la plus externe effectue les opérations suivantes :  
  
-   Elle interroge l'ensemble de lignes `SalesOrder`, spécifié dans la clause `FROM`. Le résultat est un document XML possédant un ou plusieurs éléments <`SalesOrder`>.  
  
-   Spécifie le mode `AUTO` et la directive `TYPE` . `AUTO`le mode transforme le résultat de la requête en XML, `TYPE` tandis que la directive `xml` retourne le résultat sous forme de type.  
  
-   Elle inclut deux instructions `SELECT` imbriquées séparées par une virgule. La première instruction `SELECT` imbriquée extrait les informations sur la commande, l'en-tête et les détails, tandis que la seconde instruction `SELECT` imbriquée extrait les informations sur le vendeur.  
  
    -   L'instruction `SELECT` qui extrait `SalesOrderID`, `SalesPersonID`et `CustomerID` inclut elle-même une autre instruction imbriquée `SELECT ... FOR XML` (avec le mode `AUTO` et la directive `TYPE` ) qui retourne des informations sur les détails des commandes.  
  
 L'instruction `SELECT` qui extrait les informations sur le vendeur interroge un ensemble de lignes, `SalesPerson`, créé dans la clause `FROM` . Pour que les requêtes `FOR XML` fonctionnent, vous devez fournir un nom pour l'ensemble de lignes anonyme généré dans la clause `FROM` . Dans ce cas, le nom fourni est `SalesPerson`.  
  
 Voici le résultat partiel :  
  
```  
<SalesOrder>  
  <Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  </Sales.SalesOrderHeader>  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</SalesOrder>  
...  
```  
  
 La requête suivante génère les mêmes informations sur la commande, sauf que, dans le document XML obtenu, <`SalesPerson`> apparaît en tant que frère de <`SalesOrderDetail`> :  
  
```  
<SalesOrder>  
    <SalesOrderHeader ...>  
          <SalesOrderDetail .../>  
          <SalesOrderDetail .../>  
          ...  
          <SalesPerson .../>  
    </SalesOrderHeader>  
  
</SalesOrder>  
<SalesOrder>  
  ...  
</SalesOrder>  
```  
  
 Voici la requête :  
  
```  
SELECT SalesOrderID, SalesPersonID, CustomerID,  
             (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
              from Sales.SalesOrderDetail  
              WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
              FOR XML AUTO, TYPE),  
              (SELECT *   
               FROM  (SELECT SalesPersonID, EmployeeID  
                    FROM Sales.SalesPerson, HumanResources.Employee  
                    WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
               WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
         FOR XML AUTO, TYPE)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID=43659 or SalesOrderID=43660  
FOR XML AUTO, TYPE  
```  
  
 Voici le résultat obtenu :  
  
```  
<Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
<Sales.SalesOrderHeader SalesOrderID="43660" SalesPersonID="279" CustomerID="117">  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="762" OrderQty="1" UnitPrice="419.4589" />  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="758" OrderQty="1" UnitPrice="874.7940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
```  
  
 Étant donné que la directive `TYPE` renvoie un résultat de requête de type `xml`, vous pouvez recourir à différentes méthodes de type de données `xml` pour interroger le document XML obtenu. Pour plus d’informations, consultez [Méthodes de données de type xml](/sql/t-sql/xml/xml-data-type-methods). Dans la requête suivante, notez ce qui suit :  
  
-   La requête précédente est ajoutée à la clause `FROM` . Les résultats de la requête sont renvoyés sous la forme d'une table. Notez l'ajout de l'alias `XmlCol` .  
  
-   La clause `SELECT` définit une requête XQuery par rapport à l'alias `XmlCol` renvoyé dans la clause `FROM` . La méthode `query()` du type de données `xml` est utilisée dans la spécification de la requête XQuery. Pour plus d’informations, consultez [Méthode query&#40;&#41; &#40;type de données xml&#41;](/sql/t-sql/xml/query-method-xml-data-type).  
  
    ```  
    SELECT XmlCol.query('<Root> { /* } </Root>')  
    FROM (  
    SELECT SalesOrderID, SalesPersonID, CustomerID,  
                 (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
                  from Sales.SalesOrderDetail  
                  WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
                  FOR XML AUTO, TYPE),  
                  (SELECT *   
                   FROM  (SELECT SalesPersonID, EmployeeID  
                        FROM Sales.SalesPerson, HumanResources.Employee  
                        WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
                   WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
             FOR XML AUTO, TYPE)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesOrderID='43659' or SalesOrderID='43660'  
    FOR XML AUTO, TYPE ) as T(XmlCol)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des requêtes FOR XML imbriquées](use-nested-for-xml-queries.md)  
  
  
