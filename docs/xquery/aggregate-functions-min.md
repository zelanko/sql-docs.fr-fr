---
title: Fonction min (XQuery) | Microsoft Docs
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
- fn:min function
- min function [XQuery]
ms.assetid: db0b7d94-3fa6-488f-96d6-6a9a7d6eda23
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 69381eb0ffdd3638079d824d8d4c150563375a6c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046963"
---
# <a name="aggregate-functions---min"></a>Fonctions d’agrégation : min
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Renvoie, à partir d’une séquence de valeurs atomiques, *$arg*, le seul élément dont la valeur est inférieure à celle de tous les autres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:min($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Séquence d'éléments à partir de laquelle la valeur minimale est renvoyée.  
  
## <a name="remarks"></a>Notes  
 Tous les types de valeurs atomisées transmises à **min()** doivent être des sous-types du même type de base. Types de base acceptés sont les types qui prennent en charge la **gt** opération. Ces types incluent les trois types numériques de base intégrés, les types de base date/heure et les types xs:string (chaîne), xs:boolean (booléen) et xdt:untypedAtomic (atomique non typé). Les valeurs de type xdt:untypedAtomic sont converties en xs:double. S’il existe un mélange de ces types, ou si d’autres valeurs d’autres types sont passés, une erreur statique est générée.  
  
 Le résultat de **min()** reçoit le type de base des types transmis, tels que xs : double dans le cas de xdt : untypedAtomic. Si l'entrée est statiquement vide, vide est implicite et une erreur statique est générée.  
  
 Le **min()** fonction retourne une valeur dans la séquence est inférieure à toute autre dans la séquence d’entrée. Pour les valeurs xs:string, le classement par défaut des points de code Unicode est utilisé. Si une valeur xdt : untypedAtomic ne peut pas être convertie en xs : double, la valeur est ignorée dans la séquence d’entrée, *$arg*. Si l'entrée est une séquence vide calculée de manière dynamique, la séquence vide est renvoyée.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
### <a name="a-using-the-min-xquery-function-to-find-the-work-center-location-that-has-the-fewest-labor-hours"></a>A. Utilisation de la fonction XQuery min() pour rechercher le poste de travail enregistrant le moins d'heures de main-d'œuvre  
 La requête suivante récupère tous les postes de travail du processus de fabrication du modèle de produit (ProductModelID=7) qui enregistre le moins d'heures de main-d'œuvre. Généralement, comme le montre l'exemple suivant, un seul poste est renvoyé. Si plusieurs postes de travail enregistraient le même nombre minimal de main-d'œuvre, ils seraient tous renvoyés.  
  
```  
select ProductModelID, Name, Instructions.query('  
  declare namespace AWMI=  
    "https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  for   $Location in /AWMI:root/AWMI:Location  
  where $Location/@LaborHours =  
          min( /AWMI:root/AWMI:Location/@LaborHours )  
return  
  <Location WCID=     "{ $Location/@LocationID }"   
              LaborHrs= "{ $Location/@LaborHours }" />  
  ') as Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le **espace de noms** mot clé dans le prologue XQuery définit un préfixe d’espace de noms. Ce préfixe est utilisé ultérieurement dans le corps de la requête.  
  
 Le corps XQuery construit le code XML qui a un \<emplacement > élément avec WCID et **LaborHrs** attributs.  
  
-   La requête récupère également l'identificateur et le nom du modèle de produit.  
  
 Voici le résultat obtenu :  
  
```  
ProductModelID   Name              Result  
---------------  ----------------  ---------------------------------  
7                HL Touring Frame  <Location WCID="45" LaborHrs="0.5"/>   
```  
  
## <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **min()** fonction mappe tous les entiers à xs : decimal.  
  
-   Le **min()** fonction sur les valeurs de type xs : Duration n’est pas pris en charge.  
  
-   Les séquences faisant intervenir plusieurs types dérivés de différents types de base ne sont pas prises en charge.  
  
-   L'option syntaxique fournissant un classement n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
