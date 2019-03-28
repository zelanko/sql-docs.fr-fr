---
title: 'Exemple : Spécification des Directives ID et IDREFS | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8771eb523153a2a03b7e10dd58b3c1a85504f63e
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531251"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a>Exemple : Spécification des directives ID et IDREF
  Un attribut d'élément peut être spécifié comme attribut de type `ID` et l'attribut `IDREFS` peut ensuite être utilisé pour y faire référence. Cela permet de créer des liens à l'intérieur du document et est assimilable aux relations entre clés primaires et clés étrangères dans les bases de données relationnelles.  
  
 Cet exemple illustre l'utilisation des directives `ID` et `IDREFS` pour créer des attributs de types `ID` et `IDREFS`. Étant donné que les ID ne peuvent pas être des valeurs entières, dans cet exemple, leurs valeurs sont converties. En d'autres termes, ils subissent une conversion de type. Des préfixes sont utilisés pour les valeurs d'ID.  
  
 Supposons que vous souhaitez construire un document XML comme suit :  
  
```  
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >  
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
 L'attribut `SalesOrderIDList` de l'élément < `Customer` > est un attribut à valeurs multiples qui fait référence à l'attribut `SalesOrderID` de l'élément < `SalesOrder` >. Pour établir ce lien, vous devez déclarer l’attribut `SalesOrderID` comme étant de type `ID` et l’attribut `SalesOrderIDList` de l’élément <`Customer`> comme étant de type `IDREFS`. Comme un client peut passer plusieurs commandes, le type `IDREFS` est utilisé.  
  
 Les éléments de type `IDREFS` ont également plusieurs valeurs. Par conséquent, vous devez recourir à une clause de sélection distincte qui réutilisera les mêmes informations de colonne de balise, de parent et de clé. La clause `ORDER BY` doit faire en sorte que la séquence des lignes qui composent les valeurs `IDREFS` apparaisse regroupée sous leur élément parent.  
  
 La requête ci-après génère le document XML souhaité. La requête utilise les directives `ID` et `IDREFS` pour remplacer les types dans les noms de colonne (`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID       [Customer!1!CustomerID],  
        NULL               [Customer!1!SalesOrderIDList!IDREFS],  
        NULL               [SalesOrder!2!SalesOrderID!ID],  
        NULL               [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   
UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerIDORDER BY [Customer!1!CustomerID] ,  
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode EXPLICIT avec FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
