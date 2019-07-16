---
title: ALTER CUBE Statement (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 750f8ae7a1b9275bdab734a15134d255916e7d44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098525"
---
# <a name="mdx-data-definition---alter-cube"></a>Définition de données MDX - ALTER CUBE


  Modifie la structure d'un cube spécifié, en général pour prendre en charge l'écriture différée. Pour plus d’informations sur l’utilisation de l’écriture différée dans une application, consultez ce blog : [Création d’une Application de l’écriture différée avec Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977)  
  
 Notez que les écritures différées de dimensions simultanées peuvent provoquer un blocage : la première écriture différée est bloquée par une validation en raison du verrou partagé conservé par la deuxième écriture différée. Aucune erreur n'est générée dans ce cas, mais aucune des deux d'opération ne peut progresser. Les deux opérations expirent et les modifications sont supprimées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER CUBE  
      Cube_Name | CURRENTCUBE  
      <alter clause>   
            [ < alter clause> ...n]  
  
< alter clause> ::=   
   <create dimension member clause>   
  | <remove dimension member clause>  
  | <move dimension member clause>   
    | <update clause>   
    | <create cell calculation clause>  
  
<create dimension member clause> ::=  
CREATE DIMENSION MEMBER [ParentName.]MemberName  
    , [[KEY = Key_Value]   
    | [Property_Name = Property_Value[, ...n]]  
  
<dropping clause>::=  
DROP   
      DIMENSION MEMBER Member_Name   
            Member_Name ...n ]   
      [WITH DESCENDANTS]  
      | [ SESSION ] [ CALCULATED ] MEMBER Member_Name   
                  [ ,Member_Name,...n ]   
    | SET Set_Name  
                  [ ,Set_Name,...n ]   
    | [ SESSION ] CELL CALCULATION CellCalc_Name  
                  [ ,CellCalc_Name,...n ]   
    | ACTION Action_Name  
  
<move dimension member clause> ::=  
MOVE DIMENSION MEMBER MemberName  
        [, SKIPPED_LEVELS = Unsigned_Integer]   
      [WITH DESCENDANTS]  
    UNDER ParentName      
  
<update clause> ::=  
UPDATE   
    CUSTOM ROLLUP FOR MEMBER MemberName  
      [,MemberName, ...n] AS MDX_Expression  
   | DIMENSION Dimension_Name | Hierarchy_Name  
      , DEFAULT_MEMBER = MDX_Expression  
   | DIMENSION MEMBER MemberName AS  
   [MDX_Expression]  
   [Property_Name = Property_Value[, ...n]]  
  
<create cell calculation clause>::=  
CELL CALCULATION Calculation_Name   
   FOR Set_Expression AS MDX_Expression   
            [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="creating-a-dimension-member"></a>Création d'un membre de dimension  
 Une nouvelle ligne est ajoutée à la table de dimension sous-jacente.  
  
### <a name="arguments"></a>Arguments  
 *ParentName*  
 Expression de chaîne valide fournissant le nom du parent du nouveau membre de dimension, sauf si le membre de dimension est créé à la racine.  
  
 *Nom de membre*  
 Expression de chaîne valide qui spécifie le nom d'un membre.  
  
 *É chec*  
 Expression scalaire valide qui définit la valeur de clé du nouveau membre de dimension.  
  
 *Property_name*  
 Identificateur MDX (Multidimensional Expressions) valide représentant une propriété de membre.  
  
 *Property_Value*  
 Expression scalaire MDX (Multidimensional Expressions) valide qui définit la valeur de la propriété de membre calculé.  
  
## <a name="dropping-a-dimension-member"></a>Suppression d'un membre de dimension  
 La suppression d'un membre de dimension d'une dimension activée en écriture signifie la suppression du membre et de sa ligne correspondante dans la table de dimension sous-jacente.  
  
### <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Expression de chaîne valide qui fournit le nom d'un cube.  
  
 *Member_Name*  
 Expression de chaîne valide qui précise un nom de membre ou une clé de membre.  
  
### <a name="remarks"></a>Notes  
 Si la clause WITH DESCENDANTS n'est pas utilisée, les enfants d'un membre supprimé deviennent les enfants du parent de ce dernier. Si la clause WITH DESCENDANTS n'est pas employée, tous les descendants et leurs lignes dans la table de dimension sont également supprimés.  
  
> [!NOTE]  
>  Pour plus d’informations sur la suppression de membres calculés, jeux nommés, actions et les calculs de cellules, consultez [instruction membre DROP &#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md), [DROP définir l’instruction &#40;MDX&#41;](../mdx/mdx-data-definition-drop-set.md), [Instruction d’ACTION DROP &#40;MDX&#41;](../mdx/mdx-data-definition-drop-action.md), et [instruction de calcul de cellule DROP &#40;MDX&#41;](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="updating-the-default-dimension-member"></a>Mise à jour du membre de dimension par défaut  
 Cette clause met à jour le membre par défaut d'un cube et est utilisée dans le script de calcul MDX en vue d'y définir un membre par défaut. Vous pouvez définir un membre par défaut pour la dimension de base de données, une dimension de cube ou pour la connexion d'un utilisateur. Vous pouvez également le modifier au cours d'une session.  
  
### <a name="arguments"></a>Arguments  
 *Dimension_Name*  
 Chaîne valide qui précise le nom d'une dimension.  
  
 *MDX_Expression*  
 Expression MDX valide qui retourne un membre unique.  
  
### <a name="remarks"></a>Notes  
 L'expression MDX spécifiée peut être statique ou dynamique.  
  
## <a name="moving-a-dimension-member"></a>Déplacement d'un membre de dimension  
 Une ligne est modifiée dans la table de dimension sous-jacente.  
  
### <a name="arguments"></a>Arguments  
 *ParentName*  
 Expression de chaîne valide qui fournit le nom du nouveau parent du membre de dimension déplacé.  
  
 *Nom de membre*  
 Expression de chaîne valide qui spécifie le nom d'un membre.  
  
 Unsigned_*entier*  
 Nombre valide qui précise le nombre de niveaux à ignorer.  
  
 Si la clause WITH DESCENDANTS est précisée, l'arborescence tout entière est déplacée. Si la clause WITH DESCENDANTS n'est pas spécifiée, les enfants d'un parent déplacé deviennent les enfants du parent du membre déplacé. Le déplacement a simplement pour conséquence la mise à jour des valeurs de la colonne clé parente dans la table de dimension sous-jacente.  
  
## <a name="updating-a-dimension-member"></a>Mise à jour d'un membre de dimension  
 La clause UPDATE DIMENSION MEMBER vous permet de modifier les propriétés d'un membre ainsi que la formule de membre personnalisée associée à un membre.  
  
### <a name="arguments"></a>Arguments  
 *Nom de membre*  
 Expression de chaîne valide qui spécifie le nom d'un membre.  
  
 *MDX_Expression*  
 Expression MDX valide qui retourne un membre unique.  
  
 *Property_Value*  
 Expression scalaire MDX valide qui définit la valeur de la propriété de membre calculé.  
  
## <a name="creating-a-cell-calculation"></a>Création d'un calcul de cellule  
 Pour plus d’informations sur la création d’un calcul de cellule à l’aide de l’instruction ALTER CUBE, consultez [instruction du calcul de cellule DROP &#40;MDX&#41;](../mdx/mdx-data-definition-drop-cell-calculation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données MDX &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
