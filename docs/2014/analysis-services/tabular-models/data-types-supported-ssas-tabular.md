---
title: Types de données pris en charge (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92993f7b-7243-4aec-906d-0b0379798242
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2502b65b1b13f8ed819c138fdfe429390a905a56
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939757"
---
# <a name="data-types-supported-ssas-tabular"></a>Types de données pris en charge (SSAS Tabulaire)
  Cet article décrit les types de données qui peuvent être utilisés dans des modèles tabulaires et aborde la conversion implicite de types de données lorsque des données sont calculées ou utilisées dans une formule DAX (Data Analysis Expressions).  
  
 Cet article contient les sections suivantes :  
  
-   [Types de données utilisés dans les modèles tabulaires](#bkmk_data_types)  
  
-   [Conversion de types de données implicites et explicites dans les formules DAX](#bkmk_implicit)  
  
-   [Gestion des valeurs vides, des chaînes vides et des valeurs zéro](#bkmk_hand_blanks)  
  
##  <a name="data-types-used-in-tabular-models"></a><a name="bkmk_data_types"></a>Types de données utilisés dans les modèles tabulaires  
 Les types de données suivants sont pris en charge. Lorsque vous importez des données ou utilisez une valeur dans une formule, même si la source de données d'origine contient un type de données différent, les données sont converties dans l'un des types de données suivants. Les valeurs issues des formules utilisent également ces types de données.  
  
 En règle générale, ces types de données sont implémentés pour permettre des calculs exacts dans les colonnes calculées, et les mêmes restrictions s'appliquent au reste des données dans les modèles à des fins de cohérence.  
  
 Les formats utilisés pour les nombres, devises, dates et heures doivent suivre le format que les paramètres régionaux spécifiés sur le client utilisé pour travailler sur les données du modèle. Vous pouvez utiliser les options de mise en forme du modèle pour contrôler la façon dont la valeur s'affiche.  
  
||||  
|-|-|-|  
|Type de données dans le modèle|Type de données dans DAX|Description|  
|Nombre entier|Valeur entière de 64 bits (huit octets) <sup>1, 2</sup>|Nombres qui n'ont pas de décimales. Les entiers peuvent être des nombres positifs ou négatifs, mais doivent être compris entre -9 223 372 036 854 775 808 (-2^63) et 9 223 372 036 854 775 807 (2^63-1).|  
|Nombre décimal|Nombre réel de 64 bits (huit octets) <sup>1, 2</sup>|Les nombres réels sont des nombres qui peuvent avoir des décimales. Les nombres réels couvrent une large gamme de valeurs :<br /><br /> Valeurs négatives de -1.79E +308 à -2.23E -308<br /><br /> Zéro<br /><br /> Valeurs positives de 2.23E -308 à -1.79E +308<br /><br /> Toutefois, le nombre de bits significatifs est limité à 17 chiffres décimaux.|  
|Boolean|Boolean|Valeur True ou valeur False.|  
|Texte|String|Chaîne de données caractères au format Unicode. Il peut s'agir de chaînes, de nombres ou de dates représentés dans un format texte.|  
|Date|Date/Heure|Dates et heures dans une représentation date-heure acceptée.<br /><br /> Les dates valides sont toutes les dates après le 1er mars 1900.|  
|Devise|Devise|Le type de données devise autorise des valeurs entre -922 337 203 685 477,5808 et 922 337 203 685 477,5807 avec quatre chiffres décimaux à précision fixe.|  
|N/A|Vide|Le type de données Vide (Blank) de DAX représente et remplace les valeurs Null SQL. Vous pouvez créer une valeur vide à l'aide de la fonction BLANK et tester les valeurs vides à l'aide de la fonction logique ISBLANK.|  
  
 <sup>1</sup> les formules DAX ne prennent pas en charge les types de données inférieurs à ceux répertoriés dans le tableau.  
  
 <sup>2</sup> si vous tentez d’importer des données qui ont de très grandes valeurs numériques, l’importation peut échouer avec l’erreur suivante :  
  
 Erreur de base de données en mémoire : la \<column name> colonne « » de la table « » \<table name> contient une valeur, « 1.7976931348623157 e + 308 », ce qui n’est pas pris en charge. L'opération a été annulée.  
  
 Cette erreur se produit parce que le générateur de modèles utilise cette valeur pour représenter des valeurs Null. Les valeurs de la liste suivante sont des synonymes de la valeur NULL indiquée précédemment :  
  
||  
|-|  
|Value|  
|9223372036854775807|  
|-9223372036854775808|  
|1.7976931348623158e+308|  
|2.2250738585072014e-308|  
  
 Vous devez supprimer la valeur de vos données et réessayer d'importer.  
  
> [!NOTE]  
>  Vous ne pouvez pas importer à partir d’une colonne **varchar(max)** qui contient une chaîne de plus de 131 072 caractères.  
  
### <a name="table-data-type"></a>Type de données table  
 En outre, DAX utilise un type de données *table* . Ce type de données est utilisé par DAX dans de nombreuses fonctions, comme les agrégations et les calculs Time Intelligence. Certaines fonctions nécessitent une référence à une table ; d’autres retournent une table qui peut ensuite servir d’entrée pour d’autres fonctions. Dans certaines fonctions qui nécessitent une table comme entrée, vous pouvez spécifier une expression qui correspond à une table. Pour certaines fonctions, une référence à une table de base est obligatoire. Pour plus d’informations sur les exigences relatives à des fonctions spécifiques, consultez [Référence des fonctions DAX](/dax/dax-function-reference).  
  
##  <a name="implicit-and-explicit-data-type-conversion-in-dax-formulas"></a><a name="bkmk_implicit"></a>Conversion de types de données implicites et explicites dans les formules DAX  
 Chaque fonction DAX a des exigences spécifiques quant aux types de données utilisés comme entrées et sorties. Par exemple, certaines fonctions nécessitent des entiers pour certains arguments et des dates pour d’autres. D’autres fonctions nécessitent du texte ou des tables.  
  
 Si les données de la colonne que vous spécifiez comme argument sont incompatibles avec le type de données requis par la fonction, DAX, dans de nombreux cas, retourne une erreur. Toutefois, dans la mesure du possible DAX essaie de convertir implicitement les données vers le type de données requis. Par exemple :  
  
-   Vous pouvez taper un nombre, par exemple « 123 », en tant que chaîne. DAX analysera la chaîne et tentera pour la spécifier comme un type de données de nombre.  
  
-   Vous pouvez ajouter VRAI + 1 et obtenir le résultat 2, car VRAI est converti implicitement en nombre 1 et l’opération 1 + 1 est effectuée.  
  
-   Si vous additionnez des valeurs de deux colonnes et que l’une d’elles est représentée en tant que texte ("12") et l’autre en tant que nombre (12), DAX convertit implicitement la chaîne en nombre, puis effectue l’addition pour obtenir un résultat numérique. L'expression suivante retourne 44 : = "22" + 22  
  
-   Si vous essayez de concaténer deux nombres, le complément [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] les présente sous forme de chaînes, puis effectue la concaténation. L'expression suivante retourne  "1234" : = 12 & 34  
  
 Le tableau suivant résume les conversions de types de données implicites effectuées dans les formules. En règle générale, le générateur de modèles sémantiques se comporte comme Microsoft Excel et effectue des conversions implicites chaque fois que possible lorsque nécessaire pour l'opération spécifiée.  
  
### <a name="table-of-implicit-data-conversions"></a>Tableau de conversions de données implicites  
 Le type de conversion effectué est déterminé par l’opérateur, qui convertit les valeurs dont il a besoin avant d’effectuer l’opération demandée. Ces tableaux répertorient les opérateurs et indiquent la conversion effectuée sur chaque type de données dans la colonne quand il est couplé avec le type de données dans la ligne d’intersection.  
  
> [!NOTE]  
>  Les types de données texte ne sont pas inclus dans ces tableaux. Lorsqu'un nombre est représenté dans un format texte, le générateur de modèles tente dans certains cas de déterminer le type de nombre dont il s'agit et de le représenter comme un nombre.  
  
#### <a name="addition-"></a>Addition (+)  
  
||||||  
|-|-|-|-|-|  
|Opérateur (+)|INTEGER|DEVISE|RÉEL|Date/Heure|  
|ENTIER|ENTIER|DEVISE|RÉEL|Date/Heure|  
|DEVISE|DEVISE|DEVISE|real|Date/Heure|  
|real|real|real|real|Date/Heure|  
|Date/Heure|Date/Heure|Date/Heure|Date/Heure|Date/Heure|  
  
 Par exemple, si un nombre réel est utilisé dans une opération d’addition avec des données de devise, les deux valeurs sont converties en nombre réel et le résultat retourné est un nombre réel.  
  
#### <a name="subtraction--"></a>Soustraction (-)  
 Dans le tableau suivant l'en-tête de ligne est le diminuende (côté gauche) et l'en-tête de colonne est le diminuteur (côté droit).  
  
||||||  
|-|-|-|-|-|  
|Opérateur (-)|INTEGER|DEVISE|real|Date/Heure|  
|INTEGER|INTEGER|DEVISE|real|real|  
|DEVISE|DEVISE|DEVISE|real|real|  
|real|real|real|real|real|  
|Date/Heure|Date/Heure|Date/Heure|Date/Heure|Date/Heure|  
  
 Par exemple, si une date est utilisée dans une opération de soustraction avec un autre type de données, les deux valeurs sont converties en dates et la valeur de retour est également une date.  
  
> [!NOTE]  
>  Les modèles tabulaires prennent également en charge l'opérateur unaire, - (négatif), mais cet opérateur ne change pas le type de données de l'opérande.  
  
#### <a name="multiplication-"></a>Multiplication (*)  
  
||||||  
|-|-|-|-|-|  
|Opérateur (*)|INTEGER|DEVISE|real|Date/Heure|  
|INTEGER|INTEGER|DEVISE|real|ENTIER|  
|DEVISE|DEVISE|real|DEVISE|DEVISE|  
|real|real|DEVISE|real|real|  
  
 Par exemple, si un entier est combiné à un nombre réel dans une opération de multiplication, les deux nombres sont convertis en nombres réels et la valeur de retour est également un nombre réel.  
  
#### <a name="division-"></a>Division (/)  
 Dans le tableau suivant l'en-tête de ligne est le numérateur et l'en-tête de colonne est le dénominateur.  
  
||||||  
|-|-|-|-|-|  
|Opérateur (/)<br /><br /> (Ligne/Colonne)|INTEGER|DEVISE|real|Date/Heure|  
|ENTIER|RÉEL|DEVISE|real|real|  
|DEVISE|DEVISE|real|DEVISE|real|  
|real|real|real|real|real|  
|Date/Heure|real|real|real|RÉEL|  
  
 Par exemple, si un entier est combiné avec une valeur de devise dans une opération de division, les deux valeurs sont converties en nombres réels et le résultat est également un nombre réel.  
  
#### <a name="comparison-operators"></a>Opérateurs de comparaison  
 Dans les expression de comparaison, les valeurs booléennes d'expressions sont considérées comme supérieures aux valeurs de chaîne et les valeurs de chaîne sont considérées supérieures aux valeurs numériques ou aux valeurs de date/heure ; les nombres et les valeurs de date/heure sont considérées avoir le même rang. Aucune conversion implicite n’est effectuée pour les valeurs de chaîne ou booléennes. VIDE ou une valeur vide est convertie en 0/""/faux en fonction du type de données de l’autre valeur comparée.  
  
 Les expressions DAX suivantes illustrent ce comportement :  
  
 `=IF(FALSE()>"true","Expression is true", "Expression is false")` retourne `"Expression is true"`.  
  
 `=IF("12">12,"Expression is true", "Expression is false")` retourne `"Expression is true"`.  
  
 `=IF("12"=12,"Expression is true", "Expression is false")` retourne `"Expression is false"`.  
  
 Les conversions sont effectuées implicitement pour les types numériques ou de date/heure comme décrit dans le tableau suivant :  
  
||||||  
|-|-|-|-|-|  
|Opérateur de comparaison|ENTIER|DEVISE|real|Date/Heure|  
|ENTIER|INTEGER|DEVISE|real|RÉEL|  
|DEVISE|DEVISE|DEVISE|real|RÉEL|  
|RÉEL|RÉEL|RÉEL|RÉEL|RÉEL|  
|Date/Heure|real|RÉEL|RÉEL|Date/Heure|  
  
##  <a name="handling-of-blanks-empty-strings-and-zero-values"></a><a name="bkmk_hand_blanks"></a>Gestion des valeurs vides, des chaînes vides et des valeurs zéro  
 Le traitement DAX des valeurs zéro, des valeurs Null et des chaînes vides n'est pas le même que dans Microsoft Excel et SQL Server. Cette section décrit les différences et explique la manière dont sont gérés ces types de données.  
  
 Le point essentiel à retenir est que les valeurs vides, cellules vides ou valeurs manquantes sont toutes représentées par le même nouveau type de valeur, BLANK. La façon dont les valeurs de ce type sont gérées dans des opérations telles que l'addition ou la concaténation dépend de la fonction en question. Vous pouvez également générer des vides à l’aide de la fonction VIDE, ou vérifier la présence de vides à l’aide de la fonction ESTVIDE. Les valeurs Null de base de données ne sont pas prises en charge dans un modèle sémantique, et les valeurs Null sont converties implicitement en valeurs vides (blank) lorsqu'une colonne qui contient une valeur Null est référencée dans une formule DAX.  
  
### <a name="defining-blanks-nulls-and-empty-strings"></a>Définition des valeurs vides, des valeurs Null et des chaînes vides  
 Le tableau suivant résume les différences entre DAX et Microsoft Excel quant à la façon dont les valeurs vides (blank) sont gérées.  
  
||||  
|-|-|-|  
|Expression|DAX|Excel|  
|VIDE + VIDE|VIDE|0 (zéro)|  
|BLANK +5|5|5|  
|VIDE * 5|VIDE|0 (zéro)|  
|5/VIDE|Infini|Erreur|  
|0/VIDE|NaN|Erreur|  
|VIDE/VIDE|VIDE|Erreur|  
|FAUX OU VIDE|FALSE|FALSE|  
|FAUX ET VIDE|FALSE|FALSE|  
|VRAI OU VIDE|TRUE|TRUE|  
|VRAI ET VIDE|FAUX|VRAI|  
|VIDE OU VIDE|VIDE|Erreur|  
|VIDE ET VIDE|VIDE|Erreur|  
  
 Pour plus d’informations sur la façon dont une fonction ou un opérateur spécifique gèrent les valeurs vides, voir les rubriques relatives à la fonction DAX concernée dans la section [Référence des fonctions DAX](/dax/dax-function-reference).  
  
## <a name="see-also"></a>Voir aussi  
 [Sources de données &#40;&#41;tabulaire SSAS](../data-sources-ssas-tabular.md)   
 [Importer des données &#40;SSAS Tabulaire&#41;](../import-data-ssas-tabular.md)  
  
  
