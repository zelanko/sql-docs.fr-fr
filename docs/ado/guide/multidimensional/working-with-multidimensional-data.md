---
title: Utilisation des données multidimensionnelles | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- multidimensional data [ADO]
ms.assetid: 84387746-aa3e-44fd-ad6c-a8214a6966dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a284254c058eae0362fe23860e1b406a97f0bf49
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63222494"
---
# <a name="working-with-multidimensional-data"></a>Utilisation de données multidimensionnelles
Un *cellset* est le résultat d’une requête sur des données multidimensionnelles. Il se compose d’une collection d’axes, généralement pas plus de quatre axes et généralement deux ou trois. Un *axe* est une collection de membres à partir d’une ou plusieurs dimensions, ce qui permet de rechercher ou de filtrer des valeurs spécifiques dans un cube.  
  
 Un *position* est un point le long d’un axe. Pour un axe consistant en une seule dimension, ces positions sont un sous-ensemble des membres de dimension. Si un axe comprend plusieurs dimensions, chaque position est une entité composée, ce qui a *n* parties où *n* est le nombre de dimensions orientés le long de cet axe. Chaque partie de la position est un membre d’une dimension qui le composent.  
  
 Par exemple, si les dimensions de produit et Geography à partir d’un cube contenant des données de ventes sont orientées le long de l’axe des x d’un jeu de cellules, une position le long de cet axe peut contenir les membres « USA » et « Ordinateurs ». Dans cet exemple, la détermination d’une position le long de l’axe des abscisses nécessite que les membres de chaque dimension sont orientés le long de l’axe.  
  
 Un *cellule* est un objet placé à l’intersection de coordonnées d’axe. Chaque cellule comporte plusieurs éléments d’information associés, y compris les données elles-mêmes, une chaîne mise en forme (le formulaire affichable des données de cellule) et la valeur ordinale de cellule. (Chaque cellule est une valeur ordinale unique dans l’ensemble de cellules. La valeur ordinale de la première cellule dans l’ensemble de cellules est égal à zéro, tandis que la cellule la plus à gauche de la deuxième ligne d’un jeu de cellules avec huit colonnes aurait une valeur ordinale de huit.)  
  
 Par exemple, un cube comporte les dimensions de six suivantes (Notez que ce schéma de cube est légèrement différente de celui donné [vue d’ensemble de schémas et données multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)) :  
  
-   Commercial  
  
-   Géographie (hiérarchie naturelle) - Continents, pays, États, etc.  
  
-   Trimestres-trimestres, mois, jours  
  
-   Années  
  
-   Mesures - ventes, ChangementPourcentage, VentesBudget  
  
-   Products  
  
 L’ensemble de cellules suivant représente les ventes pour 1991 pour tous les produits :  
  
> [!NOTE]
>  Les valeurs de cellule dans l’exemple peuvent être considérés comme paires ordonnées de valeurs ordinales de position où le premier chiffre représente la position de l’axe des abscisses et le deuxième chiffre la position de l’axe des y.  
  
 Les caractéristiques de cet ensemble de cellules sont les suivantes :  
  
-   Dimensions d’axe : Trimestres, vendeur, Geography  
  
-   Dimensions de filtre : Mesures, années, produits  
  
-   Deux axes : COLONNE (x, ou axe 0) et ligne (y ou axe 1)  
  
-   l’axe des x : deux dimensions imbriquées, vendeur et géographie  
  
-   axe des y : Dimension trimestres  
  
 L’axe des x comporte deux dimensions imbriquées : Vendeur et géographie. À partir de la géographie, quatre membres sont sélectionnées : Seattle, Boston, USA-Sud et le Japon. Deux membres vendeur sont sélectionnés : Valentine et Nash. Il en résulte un total de huit positions sur cet axe (8 = 4 * 2).  
  
 Chaque coordonnée est représentée comme une position avec deux membres - un à partir de la dimension vendeur et l’autre à partir de la dimension Geography :  
  
```console
(Valentine, Seattle), (Valentine, Boston), (Valentine, USA_North),  
(Valentine, Japan), (Nash, Seattle), (Nash, Boston), (Nash, USA_North),  
(Nash, Japan)  
```  
  
 L’axe des y n'a qu’une seule, contenant les huit positions suivantes :  
  
```console
Jan, Feb, Mar, Qtr2, Qtr3, Oct, Nov, Dec  
```  
  
 Ensembles de cellules, les cellules, les axes et les positions sont toutes représentées dans ADO MD par objets correspondants : [Ensemble de cellules](../../../ado/reference/ado-md-api/cellset-object-ado-md.md), [cellule](../../../ado/reference/ado-md-api/cell-object-ado-md.md), [axe](../../../ado/reference/ado-md-api/axis-object-ado-md.md), et [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO multidimensionnel (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Vue d’ensemble des données et des schémas multidimensionnels](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [Programmation avec ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Utilisation d’ADO avec ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)
