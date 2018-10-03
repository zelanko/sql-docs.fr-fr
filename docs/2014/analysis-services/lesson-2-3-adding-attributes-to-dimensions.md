---
title: Ajout d’attributs aux Dimensions | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 80ca92d824c6832c42161a00a0b1f59884f26880
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075329"
---
# <a name="adding-attributes-to-dimensions"></a>Ajout d'attributs aux dimensions
  Une fois les dimensions définies, vous pouvez les remplir avec les attributs qui représentent chaque élément de données dans la dimension. Les attributs reposent généralement sur les champs d'une vue de source de données. Lorsque vous ajoutez des attributs à une dimension, vous pouvez inclure des champs de n'importe quelle table dans la vue de source de données.  
  
 Dans cette tâche, vous utiliserez le Concepteur de dimensions pour ajouter des attributs aux dimensions Customer et Product. La dimension Customer inclut des attributs basés sur des champs des deux tables Customer et Geography.  
  
## <a name="adding-attributes-to-the-customer-dimension"></a>Ajout d'attributs à la dimension Customer  
  
#### <a name="to-add-attributes"></a>Pour ajouter des attributs  
  
1.  Ouvrez le Concepteur de dimensions pour la dimension Customer. Pour cela, double-cliquez sur la dimension **Customer** du nœud **Dimensions** de l’Explorateur de solutions.  
  
2.  Dans le volet **Attributs** , remarquez les attributs Customer Key et Geography Key créés par l'Assistant Cube.  
  
3.  Dans la barre d'outils de l'onglet **Structure de dimension** , assurez-vous que l'icône Zoom qui permet d'afficher les tables du volet **Vue de source de données** est définie avec un zoom de 100 %.  
  
4.  Faites glisser les colonnes suivantes de la table **Customer** du volet **Vue de source de données** vers le volet **Attributs** :  
  
    -   **BirthDate**  
  
    -   **MaritalStatus**  
  
    -   **Gender**  
  
    -   **EmailAddress**  
  
    -   **YearlyIncome**  
  
    -   **TotalChildren**  
  
    -   **NumberChildrenAtHome**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **HouseOwnerFlag**  
  
    -   **NumberCarsOwned**  
  
    -   **Téléphone**  
  
    -   **DateFirstPurchase**  
  
    -   **CommuteDistance**  
  
5.  Faites glisser les colonnes suivantes de la table **Geography** du volet **Vue de source de données** vers le volet **Attributs** :  
  
    -   **Ville**  
  
    -   **StateProvinceName**  
  
    -   **EnglishCountryRegionName**  
  
    -   **PostalCode**  
  
6.  Dans le menu Fichier, cliquez sur **Enregistrer tout**.  
  
## <a name="adding-attributes-to-the-product-dimension"></a>Ajout d'attributs à la dimension Product  
  
#### <a name="to-add-attributes"></a>Pour ajouter des attributs  
  
1.  Ouvrez le Concepteur de dimensions pour la dimension Product. Double-cliquez sur la dimension **Product** dans l’Explorateur de solutions.  
  
2.  Dans le volet **Attributs** , remarquez que l'attribut Product Key été créé par l'Assistant Cube.  
  
3.  Dans la barre d'outils de l'onglet **Structure de dimension** , assurez-vous que l'icône Zoom qui permet d'afficher les tables du volet **Vue de source de données** est définie avec un zoom de 100 %.  
  
4.  Faites glisser les colonnes suivantes de la table **Product** du volet **Vue de source de données** vers le volet **Attributs** :  
  
    -   **StandardCost**  
  
    -   **Color**  
  
    -   **SafetyStockLevel**  
  
    -   **ReorderPoint**  
  
    -   **ListPrice**  
  
    -   **Taille**  
  
    -   **SizeRange**  
  
    -   **Weight**  
  
    -   **DaysToManufacture**  
  
    -   **ProductLine**  
  
    -   **DealerPrice**  
  
    -   **Classe**  
  
    -   **Style**  
  
    -   **ModelName**  
  
    -   **StartDate**  
  
    -   **EndDate**  
  
    -   **État**  
  
5.  Dans le menu Fichier, cliquez sur **Enregistrer tout**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Vérification des propriétés de cube et de dimension](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d’attribut de dimension](multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
