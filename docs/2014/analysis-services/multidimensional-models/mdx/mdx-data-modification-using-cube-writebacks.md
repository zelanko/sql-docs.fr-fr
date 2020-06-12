---
title: Utilisation d’écritures différées de cube (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- writeback [Analysis Services], cubes
- cubes [Analysis Services], modifying
- modifying cubes
- UPDATE CUBE statement
- cubes [Analysis Services], writeback
ms.assetid: ae2385fc-7fa0-4f8e-98d7-dcb0a5f0eeea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3ac43e9206619117c1fc090a594ca32ccbeeeb31
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546331"
---
# <a name="using-cube-writebacks-mdx"></a>Utilisation de l'écriture différée de cubes (MDX)
  Pour mettre à jour un cube, vous pouvez utiliser l’instruction [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) . Celle-ci permet de mettre à jour un tuple avec une valeur spécifique. Pour utiliser efficacement l'instruction UPDATE CUBE afin de mettre à jour un cube, vous devez comprendre la syntaxe de l'instruction, les conditions d'erreur susceptibles de se produire, ainsi que les effets potentiels des mises à jour sur un cube.  
  
## <a name="update-cube-statement-syntax"></a>Syntaxe de l'instruction UPDATE CUBE  
 La syntaxe suivante décrit l'instruction UPDATE CUBE :  
  
```  
UPDATE [CUBE] <Cube_Name> SET <tuple>.VALUE = <value> [,<tuple>.VALUE = <value>...]  
 [ USE_EQUAL_ALLOCATION | USE_EQUAL_INCREMENT |  
  USE_WEIGHTED_ALLOCATION [BY <weight value_expression>] |  
  USE_WEIGHTED_INCREMENT [BY <weight value_expression>] ]   
```  
  
 Si un jeu complet de coordonnées n'est pas spécifié pour le tuple, les coordonnées non spécifiées utilisent le membre par défaut de la hiérarchie. Le tuple identifié doit faire référence à une cellule agrégée avec la fonction [Sum](/sql/mdx/sum-mdx) , et ne doit pas utiliser de membre calculé comme l’une des coordonnées de la cellule.  
  
 Vous pouvez considérer l'instruction UPDATE CUBE comme une sous-routine générant une série d'opérations d'écriture différée isolées sur des cellules atomiques. Toutes ces opérations d'écriture différée sont ensuite regroupées dans la somme spécifiée.  
  
> [!NOTE]  
>  Lorsque les cellules mises à jour ne se chevauchent pas, la propriété de chaîne de connexion `Update Isolation Level` peut être utilisée pour améliorer les performances pour UPDATE CUBE. Pour plus d’informations, consultez <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.  
  
## <a name="example"></a>Exemple  
 Pour tester l'instruction UPDATE CUBE, utilisez le groupe de mesures Cibles de ventes dans le cube Adventure Works. Ce groupe de mesures est constitué de mesures regroupées par SUM, qui est une condition requise pour l'instruction UPDATE CUBE.  
  
1.  Activez l'écriture différée pour le groupe de mesures Cibles de ventes dans la base de données Adventure Works. Dans Management Studio, cliquez avec le bouton droit sur un groupe de mesures, pointez sur **Options d’écriture différée**et sélectionnez **Activer l’écriture différée**.  
  
     Une nouvelle table d'écriture différée doit s'afficher dans le dossier d'écriture différée. Le nom de table est WriteTable_Fact Sales Quota.  
  
2.  Ouvrez une fenêtre de requête MDX. Exécutez l'instruction SELECT ci-dessous pour afficher la valeur d'origine :  
  
    ```  
    SELECT [Measures].[Sales Amount Quota] on 0 ,  
    [Employee].[Employee Department].[Title].&[Sales Representative].children on 1  
    FROM [Adventure Works]  
  
    ```  
  
     Les quotas sur le montant des ventes doivent s'afficher pour chaque représentant.  
  
3.  Exécutez l'instruction UPDATE CUBE pour l'écriture différée d'une nouvelle valeur. Dans cet exemple, nous définissons le quota du montant des ventes à 0. Dans la mesure où la nouvelle valeur est 0, ne spécifiez pas de méthode d'allocation.  
  
    ```  
    UPDATE CUBE [Adventure Works]   
    SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 0  
  
    ```  
  
4.  Réexécutez l'instruction SELECT. Zéro doit s'afficher pour les quotas.  
  
 La valeur d'écriture différée est contrainte à la session active. Pour rendre la valeur persistante entre les utilisateurs et les sessions, traitez la table d'écriture différée. Dans Management Studio, cliquez avec le bouton droit sur WriteTable_Fact Sales Quota et sélectionnez **Traiter**.  
  
 Pour spécifier une méthode d'allocation, la nouvelle valeur doit être supérieure à zéro. Dans cet exemple, la nouvelle valeur du quota du montant des ventes est de deux millions et la méthode d'allocation distribue le montant à tous les représentants.  
  
```  
UPDATE CUBE [Adventure Works]   
SET ([Measures].[Sales Amount Quota], [Employee].[Employee Department].[Department].&[Sales]) = 2000000   
USE_EQUAL_ALLOCATION  
```  
  
## <a name="error-conditions"></a>Conditions d'erreur  
 Le tableau suivant décrit à la fois les éléments pouvant entraîner l'échec d'écritures différées et le résultat de ces erreurs.  
  
|Condition d'erreur|Résultats|  
|---------------------|------------|  
|La mise à jour comprend les membres de la même dimension qui n'existent pas l'un avec l'autre.|La mise à jour échoue. L'espace du cube ne contient pas la cellule référencée.|  
|La mise à jour comprend une mesure provenant d'une mesure de type non signé.|La mise à jour échoue. Les incréments exigent que la mesure puisse accepter une valeur négative.|  
|La mise à jour comprend une mesure d'agrégation de type autre que somme.|Une erreur est générée.|  
|Vous avez tenté d'exécuter la mesure sur un sous-cube.|Une erreur est générée.|  
  
## <a name="affect-of-cube-changes"></a>Effets des modifications apportées au cube  
 Les modifications suivantes n'ont aucun effet sur une écriture différée :  
  
-   traitement d'un cube, de ses groupes de mesures du cube ou de ses dimensions ;  
  
-   ajout d'attributs à une dimension quelconque ;  
  
-   ajoute d'une nouvelle dimension ;  
  
-   suppression d'une dimension qui ne comprend pas l'écriture différée ;  
  
-   ajout, modification ou suppression d'une hiérarchie ;  
  
-   ajout d'une nouvelle mesure.  
  
 Les modifications suivantes ne peuvent pas être effectuées sans supprimer les données en écriture différée :  
  
-   suppression d'un attribut, de sa hiérarchie d'attribut, s'il est compris dans l'écriture différée. Cela inclut la suppression explicite de l'attribut, ou de sa hiérarchie d'attribut, ou encore la suppression de la dimension parente de l'attribut ;  
  
-   suppression d'une mesure comprise dans l'écriture différée ;  
  
-   ajout d'un attribut dépourvu de niveau `(All)` à une dimension comprise dans l'écriture différée ;  
  
-   modification de la granularité d'une dimension comprise dans l'écriture différée.  
  
## <a name="see-also"></a>Voir aussi  
 [Modification de données &#40;MDX&#41;](mdx-data-modification-modifying-data.md)  
  
  
