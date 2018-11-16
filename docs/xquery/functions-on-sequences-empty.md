---
title: vide la fonction (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- empty function
- fn:empty function
ms.assetid: 46da89a8-0cd9-4913-8521-4087589a04ba
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5d9afc542b8d743c3e4e0ae35bb87f10e2f0835f
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669358"
---
# <a name="functions-on-sequences---empty"></a>Fonctions sur les séquences : empty
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur True si la valeur de *$arg* est une séquence vide. Sinon, cette fonction renvoie la valeur False.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:empty($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Séquence d'éléments. Si la séquence est vide, la fonction renvoie la valeur True. Sinon, cette fonction renvoie la valeur False.  
  
## <a name="remarks"></a>Notes  
 Le **fn :EXISTS()** fonction n’est pas prise en charge. Comme alternative, la **not()** fonction peut être utilisée.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
### <a name="a-using-the-empty-xquery-function-to-determine-if-an-attribute-is-present"></a>A. Utilisation de la fonction XQuery empty() pour déterminer la présence d'un attribut  
 Dans le processus de fabrication du modèle de produit 7, cette requête retourne tous les postes de travail qui n’ont pas un **MachineHours** attribut.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /AWMI:root/AWMI:Location[empty(@MachineHours)]  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
              $i/@MachineHours  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Voici le résultat obtenu :  
  
```  
ProductModelID      Result          
-------------- ------------------------------------------  
7              <Location LocationID="30" LaborHrs="1"/>  
               <Location LocationID="50" LaborHrs="3"/>  
               <Location LocationID="60" LaborHrs="4"/>  
```  
  
 La requête suivante, légèrement modifiée, renvoie « NotFound » si le **Machinehours** attribut n’est pas présent :  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace p14="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /p14:root/p14:Location  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
                 if (empty($i/@MachineHours)) then  
                    attribute MachineHours { "NotFound" }  
                 else  
                    attribute MachineHours { data($i/@MachineHours) }  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Voici le résultat obtenu :  
  
```  
ProductModelID Result                         
-------------- -----------------------------------  
7                
  <Location LocationID="10" LaborHrs="2.5" MachineHours="3"/>  
  <Location LocationID="20" LaborHrs="1.75" MachineHours="2"/>  
  <Location LocationID="30" LaborHrs="1" MachineHours="NotFound"/>  
  <Location LocationID="45" LaborHrs="0.5" MachineHours="0.65"/>  
  <Location LocationID="50" LaborHrs="3" MachineHours="NotFound"/>  
  <Location LocationID="60" LaborHrs="4" MachineHours="NotFound"/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery impliquant le Type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [Méthode exist&#40;&#41; &#40;type de données xml&#41;](../t-sql/xml/exist-method-xml-data-type.md)  
  
  
