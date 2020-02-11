---
title: Utilisation des propriétés de cellule (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- intrinsic cell properties [MDX]
- cells [MDX]
- cell properties [MDX]
- CELL PROPERTIES keyword
ms.assetid: a593c74d-8c5e-485e-bd92-08f9d22451d4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c2c3d4838d0e21a1520197612dd08c679df843a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074340"
---
# <a name="using-cell-properties-mdx"></a>Utilisation des propriétés de cellule (MDX)
  Les propriétés de cellule dans les expressions multidimensionnelles (MDX, Multidimensional Expressions) contiennent des informations sur le contenu et le format des cellules appartenant à une source de données multidimensionnelles, par exemple un cube.  
  
 La syntaxe MDX prend en charge le mot clé CELL PROPERTIES dans une instruction MDX SELECT pour l'extraction des propriétés de cellule intrinsèques. Ces propriétés sont principalement utilisées pour définir l'affichage des données des cellules.  
  
## <a name="cell-properties-keyword-syntax"></a>Syntaxe du mot clé CELL PROPERTIES  
 Utilisez la syntaxe suivante pour le mot clé `CELL PROPERTIES` de l'instruction MDX  `SELECT` :  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 La syntaxe suivante représente le format de la valeur `<cell_props>` et la manière dont elle utilise le mot clé `CELL PROPERTIES` avec une ou plusieurs propriétés de cellule intrinsèques :  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a>Propriétés de cellule intrinsèques prises en charge  
 Le tableau suivant dresse la liste des propriétés de cellule intrinsèques prises en charge utilisées dans la valeur `<property>` .  
  
|Propriété|Description|  
|--------------|-----------------|  
|`ACTION_TYPE`|Masque binaire indiquant les types d'actions qui existent sur la cellule. Cette propriété peut prendre les valeurs suivantes :<br /><br /> **MDACTION_TYPE_URL**<br /><br /> **MDACTION_TYPE_HTML**<br /><br /> **MDACTION_TYPE_STATEMENT**<br /><br /> **MDACTION_TYPE_DATASET**<br /><br /> **MDACTION_TYPE_ROWSET**<br /><br /> **MDACTION_TYPE_COMMANDLINE**<br /><br /> **MDACTION_TYPE_PROPRIETARY**<br /><br /> **MDACTION_TYPE_REPORT**<br /><br /> **MDACTION_TYPE_DRILLTHROUGH**<br /><br /> <br /><br /> Remarque : les actions d’extraction des requêtes dont la clause Where contient un jeu ne sont pas comprises.|  
|**BACK_COLOR**|Couleur d'arrière-plan utilisée pour afficher la propriété `VALUE` ou `FORMATTED_VALUE`. Pour plus d’informations, consultez [Contenu de FORE_COLOR et BACK_COLOR &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|`CELL_ORDINAL`|Numéro ordinal de la cellule dans le jeu de données.|  
|**FONT_FLAGS**|Masque de bits détaillant les effets sur la police. Par exemple, la valeur 5 représente la combinaison des effets gras (`MDFF_BOLD`) et souligné (`MDFF_UNDERLINE`). La valeur de cette propriété est le résultat d'une opération OU au niveau du bit sur une ou plusieurs des constantes suivantes :<br /><br /> `MDFF_BOLD`= 1<br /><br /> 
  `MDFF_ITALIC` = 2<br /><br /> 
  `MDFF_UNDERLINE` = 4<br /><br /> 
  `MDFF_STRIKEOUT` = 8|  
|**FONT_NAME**|Police à utiliser pour afficher la propriété `VALUE` ou `FORMATTED_VALUE`.|  
|**FONT_SIZE**|Taille de la police à utiliser pour afficher la propriété `VALUE` ou `FORMATTED_VALUE`.|  
|**FORE_COLOR**|Couleur d'avant-plan utilisée pour afficher la propriété `VALUE` ou `FORMATTED_VALUE`. Pour plus d’informations, consultez [Contenu de FORE_COLOR et BACK_COLOR &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|`FORMAT`|Identique à `FORMAT_STRING`.|  
|`FORMAT_STRING`|Chaîne de format utilisée pour créer la valeur de la propriété `FORMATTED_VALUE`. Pour plus d’informations, consultez [Contenu de FORMAT_STRING &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md).|  
|`FORMATTED_VALUE`|Chaîne de caractères représentant un affichage avec mise en forme de la propriété `VALUE`.|  
|`LANGUAGE`|Paramètre régional auquel `FORMAT_STRING` sera appliqué. 
  `LANGUAGE` est généralement utilisé pour la conversion de devises.|  
|`UPDATEABLE`|Valeur indiquant si la cellule peut être mise à jour. Cette propriété peut prendre les valeurs suivantes :<br /><br /> `MD_MASK_ENABLED`(0x00000000) la cellule peut être mise à jour.<br /><br /> `MD_MASK_NOT_ENABLED`(0x10000000) la cellule ne peut pas être mise à jour.<br /><br /> `CELL_UPDATE_ENABLED`(0x00000001) la cellule peut être mise à jour dans l’CellSet.<br /><br /> `CELL_UPDATE_ENABLED_WITH_UPDATE`(0x00000002) la cellule peut être mise à jour avec une instruction Update. La mise à jour peut échouer si une cellule feuille non activée en écriture est mise à jour.<br /><br /> `CELL_UPDATE_NOT_ENABLED_FORMULA`(0x10000001) la cellule ne peut pas être mise à jour parce que la cellule a un membre calculé parmi ses coordonnées ; la cellule a été récupérée avec un jeu dans la clause WHERE. Une cellule peut être mise à jour même si une formule affecte sa valeur (se trouve à un certain endroit sur le chemin d'agrégation) ou si une cellule calculée se trouve dessus. Dans ce scénario, la valeur finale de la cellule ne peut pas être la valeur mise à jour, car le calcul affectera le résultat.<br /><br /> `CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE`(0x10000002) la cellule ne peut pas être mise à jour, car les mesures qui ne sont pas des sommes (Count, min, Max, distinct Count, semi-additive) ne peuvent pas être mises à jour.<br /><br /> `CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE`(0x10000003) la cellule ne peut pas être mise à jour, car elle n’existe pas, car elle se trouve à l’intersection d’une mesure et d’un membre de dimension qui n’est pas lié au groupe de mesures de la mesure.<br /><br /> `CELL_UPDATE_NOT_ENABLED_SECURE`(0x10000005) la cellule ne peut pas être mise à jour parce que la cellule est sécurisée.<br /><br /> `CELL_UPDATE_NOT_ENABLED_CALCLEVEL`(0x10000006) réservé pour une utilisation ultérieure.<br /><br /> `CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE`(0x10000007) la cellule ne peut pas être mise à jour pour des raisons internes.<br /><br /> `CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE`(0x10000009) la cellule ne peut pas être mise à jour car la mise à jour n’est pas prise en charge dans les dimensions de modèle d’exploration de données, indirect ou d’exploration de données.|  
|`VALUE`|Valeur sans mise en forme de la cellule.|  
  
 Seules les propriétés de cellule `CELL_ORDINAL`, `FORMATTED_VALUE` et `VALUE` sont obligatoires. Toutes les propriétés de cellule, intrinsèques ou propres aux fournisseurs, sont définies dans le jeu de lignes du schéma `PROPERTIES`, notamment les types de données et la prise en charge par un fournisseur. Pour plus d’informations sur `PROPERTIES` l’ensemble de lignes de schéma, consultez [MDSCHEMA_PROPERTIES rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-properties-rowset).  
  
 Par défaut, si le mot clé `CELL PROPERTIES` n'est pas utilisé, les propriétés de cellule retournées sont, dans l'ordre : `VALUE`, `FORMATTED_VALUE` et `CELL_ORDINAL`. Si le mot clé `CELL PROPERTIES` est utilisé, seules les propriétés de cellule explicitement spécifiées avec le mot clé sont retournées.  
  
 L'exemple suivant illustre l'utilisation du mot clé `CELL PROPERTIES` dans une requête MDX :  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 Les requêtes MDX qui retournent des jeux de lignes réduits ne retournent pas de propriétés de cellule ; dans ce cas, chaque cellule est représentée comme si seule la propriété de cellule `FORMATTED_VALUE` était retournée.  
  
## <a name="setting-cell-properties"></a>Définition de propriétés de cellule  
 Les propriétés de cellule peuvent être [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] définies dans à différents endroits. Par exemple, la propriété de chaîne de format peut être définie pour des mesures ordinaires sous l’onglet Structure de cube de l’éditeur de cube dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]; cette même propriété peut être définie pour des mesures calculées définies sur le cube sous l’onglet Calculs de l’éditeur de cube ; c’est également à cet emplacement que la chaîne de format des mesures calculées définies dans la clause WITH d’une requête est définie. La requête suivante montre comment les propriétés de cellule peuvent être définies sur une mesure calculée :  
  
```  
WITH MEMBER MEASURES.CELLPROPERTYDEMO AS [Measures].[Internet Sales Amount]  
, FORE_COLOR=RGB(0,0,255)  
, BACK_COLOR=IIF([Measures].[Internet Sales Amount]>7000000, RGB(255,0,0), RGB(0,255,0))  
, FONT_SIZE=10  
, FORMAT_STRING='#,#.000'  
SELECT MEASURES.CELLPROPERTYDEMO ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS ON 1  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORE_COLOR, BACK_COLOR, FONT_SIZE  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base des requêtes MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
