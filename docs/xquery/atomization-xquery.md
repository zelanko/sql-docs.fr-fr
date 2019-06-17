---
title: ATOMISATION (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, atomization
- atomization [XQuery]
ms.assetid: e3d7cf2f-c6fb-43c2-8538-4470a6375af5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bddb70c6c79ab983d1931bb17c741ff0dd531857
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047593"
---
# <a name="atomization-xquery"></a>Atomisation (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L'atomisation correspond au procédé d'extraction de la valeur typée d'un élément. Ce procédé s'applique cependant sous certaines conditions. Certains opérateurs XQuery, tels que les opérateurs arithmétiques et de comparaison, dépendent de ce processus. Par exemple, lorsque vous appliquez des opérateurs arithmétiques directement aux nœuds, la valeur typée d’un nœud est d’abord récupérée par l’appel implicite le [fonction données](../xquery/data-accessor-functions-data-xquery.md). Ceci permet de transférer la valeur atomique sous forme d'opérande à l'opérateur arithmétique.  
  
 Par exemple, la requête suivante renvoie le total des attributs LaborHours indiquant le nombre d'heures travaillées. Dans ce cas, **data()** est appliquée implicitement pour les nœuds d’attribut.  
  
```  
declare @x xml  
set @x='<ROOT><Location LID="1" SetupTime="1.1" LaborHours="3.3" />  
<Location LID="2" SetupTime="1.0" LaborHours="5" />  
<Location LID="3" SetupTime="2.1" LaborHours="4" />  
</ROOT>'  
-- data() implicitly applied to the attribute node sequence.  
SELECT @x.query('sum(/ROOT/Location/@LaborHours)')  
```  
  
 Bien que non obligatoire, vous pouvez également spécifier explicitement le **data()** fonction :  
  
```  
SELECT @x.query('sum(data(ROOT/Location/@LaborHours))')  
```  
  
 Un autre exemple d'atomisation implicite réside dans l'utilisation d'opérateurs arithmétiques. Le **+** opérateur requiert des valeurs atomiques et **data()** est appliquée implicitement pour extraire la valeur atomique de l’attribut LaborHours. La requête est spécifiée sur la colonne Instructions de la **xml** type dans la table ProductModel. La requête suivante renvoie trois fois l'attribut LaborHours. À ce sujet, vous remarquerez que :  
  
-   Lors de la construction de l'attribut OriginalLaborHours, l'atomisation s'applique implicitement à la séquence singleton renvoyée par (`$WC/@LaborHours`). La valeur typée de l'attribut LaborHours est affectée à OriginalLaborHours.  
  
-   Lors de la construction de l'attribut UpdatedLaborHoursV1, l'opérateur arithmétique requiert des valeurs atomiques. Par conséquent, **data()** s’applique implicitement à l’attribut LaborHours renvoyé par (`$WC/@LaborHours`). La valeur atomique 1 lui est ensuite ajoutée. La construction de l’attribut UpdatedLaborHoursV2 affiche l’application explicite de **data()** , mais n’est pas obligatoire.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location[1]  
        return  
            <WC OriginalLaborHours = "{ $WC/@LaborHours }"  
                UpdatedLaborHoursV1 = "{ $WC/@LaborHours + 1 }"   
                UpdatedLaborHoursV2 = "{ data($WC/@LaborHours) + 1 }" >  
            </WC>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Voici le résultat obtenu :  
  
```  
<WC OriginalLaborHours="2.5"   
    UpdatedLaborHoursV1="3.5"   
    UpdatedLaborHoursV2="3.5" />  
```  
  
 L'atomisation entraîne donc une instance d'un type simple, un ensemble vide ou une erreur de type statique.  
  
 L’atomisation se produit également dans les paramètres d’expressions de comparaison passés aux fonctions, les valeurs retournées par les fonctions, **cast()** expressions et les expressions de tri transmises dans l’ordre par clause.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes fondamentaux de XQuery](../xquery/xquery-basics.md)   
 [Expressions de comparaison &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)   
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
