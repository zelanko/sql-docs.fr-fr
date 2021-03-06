---
title: Opérateurs XQuery sur le type de données XML | Microsoft Docs
description: En savoir plus sur les opérateurs XQuery qui peuvent être utilisés avec le type de données XML.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, operators
- operators [XQuery]
- xml data type [SQL Server], XQuery
ms.assetid: 39ca3d2e-e928-4333-872b-75c4ccde8e79
author: rothja
ms.author: jroth
ms.openlocfilehash: d3fc0fece7f57957f38344a557c88fbedb908090
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730951"
---
# <a name="xquery-operators-against-the-xml-data-type"></a>Opérateurs XQuery sur le type de données xml
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  XQuery prend en charge les opérateurs suivants :  
  
-   Opérateurs numériques (+, -, *, div, mod)  
  
-   Opérateurs de comparaison de valeurs (eq, ne, lt, gt, le, ge)  
  
-   Opérateurs pour la comparaison générale (=, ! =, \<, > , \<=, > =)  
  
 Pour plus d’informations sur ces opérateurs, consultez [expressions de comparaison &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-general-operators"></a>R. Utilisation d'opérateurs généraux  
 La requête illustre l'utilisation d'opérateurs généraux qui s'appliquent à des séquences et qui comparent également des séquences. La requête récupère une séquence de numéros de téléphone pour chaque client à partir de la colonne **AdditionalContactInfo** de la table **contact** . Cette séquence est ensuite comparée à la séquence de deux numéros de téléphone ("111-111-1111", "222-2222").  
  
 La requête utilise l' **=** opérateur de comparaison. Chaque nœud de la séquence situé à droite de l' **=** opérateur est comparé à chaque nœud de la séquence sur le côté gauche. Si les nœuds correspondent, la comparaison de nœuds a la **valeur true**. Elle est ensuite convertie en int et comparée à 1, puis la requête retourne l'ID de client.  
  
```sql
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS ACI,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.value('  
      //ACI:AdditionalContactInfo//ACT:telephoneNumber/ACT:number =   
          ("111-111-1111", "222-2222")',  
      'bit')= cast(1 as bit)  
```  
  
 Il existe une autre méthode pour observer le fonctionnement de la requête précédente : chaque valeur de numéro de téléphone Récupérée à partir de la colonne **AdditionalContactInfo** est comparée à l’ensemble de deux numéros de téléphone. Si la valeur se trouve dans le jeu, le client correspondant est retourné dans le résultat.  
  
### <a name="b-using-a-numeric-operator"></a>B. Utilisation d'un opérateur numérique  
 L'opérateur + de cette requête est un opérateur de valeur, car il s'applique à un seul élément. Par exemple, la valeur 1 est ajoutée à une taille de lot retournée par la requête :  
  
```sql
SELECT ProductModelID, Instructions.query('  
     declare namespace   
 AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in (/AWMI:root/AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"  
                   LotSize  = "{  number($i/@LotSize) }"  
                   LotSize2 = "{ number($i/@LotSize) + 1 }"  
                   LotSize3 = "{ number($i/@LotSize) + 2 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
### <a name="c-using-a-value-operator"></a>C. Utilisation d'un opérateur de valeur  
 La requête suivante récupère les `Picture` éléments de> <pour un modèle de produit où la taille de l’image est « petite » :  
  
```sql
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]  
     return  
           $P  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Étant donné que les deux opérandes de l’opérateur **EQ** sont des valeurs atomiques, l’opérateur de valeur est utilisé dans la requête. Vous pouvez écrire la même requête à l’aide de l’opérateur de comparaison général ( **=** ).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery sur le type de données XML](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [SQL Server de &#40;de données XML&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Références relatives au langage Xquery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
