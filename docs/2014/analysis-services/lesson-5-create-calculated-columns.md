---
title: 'Leçon 6 : créer des colonnes calculées | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58ba761f3e32f13ddcf81dc9875057195298c705
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078561"
---
# <a name="lesson-6-create-calculated-columns"></a>Leçon 6 : Créer des colonnes calculées
  Dans cette leçon, vous allez créer des données dans votre modèle en ajoutant des colonnes calculées. Une colonne calculée est basée sur les données qui existent déjà dans votre modèle. Pour en savoir plus, consultez [Colonnes calculées &#40;SSAS Tabulaire&#41;](tabular-models/ssas-calculated-columns.md).  
  
 Vous allez créer cinq colonnes calculées dans trois tables différentes. Les étapes sont légèrement différentes pour chaque tâche. Il s’agit ici de montrer qu’il existe plusieurs façons de créer des colonnes, de les renommer, puis de les placer à différents emplacements dans une table.  
  
 Durée estimée pour suivre cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 5 : Créer des relations](lesson-4-create-relationships.md).  
  
## <a name="create-calculated-columns"></a>Créer des colonnes calculées  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a>Créer une colonne calculée de calendrier mensuel dans la table Date  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis pointez sur **Vue du modèle**et sur **Vue de données**.  
  
     Les colonnes calculées peuvent uniquement être créées à l’aide du Concepteur de modèles dans la vue de données.  
  
2.  Dans le concepteur de modèles, cliquez sur la table **Date** (onglet).  
  
3.  Cliquez avec le bouton droit sur la colonne **calendrier Quarter** , puis cliquez sur **Insérer une colonne**.  
  
     Une nouvelle colonne nommée **CalculatedColumn1** est insérée à gauche de la colonne **Calendar Quarter** .  
  
4.  Dans la barre de formule au-dessus de la table, tapez la formule suivante. La saisie semi-automatique vous aide à taper les noms complets de colonnes et de tables, et répertorie les fonctions disponibles.  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
     Les valeurs remplissent alors toutes les lignes de la colonne calculée. Si vous faites défiler la table vers le bas, vous remarquez que les lignes peuvent avoir des valeurs différentes pour cette colonne, en fonction des données figurant dans chaque ligne.  
  
    > [!NOTE]  
    >  Si vous obtenez une erreur, vérifiez que les noms de colonne dans la formule correspondent aux noms de colonne que vous avez modifiés dans la [Leçon 3 : Renommer des colonnes](rename-columns.md).  
  
5.  Renommez cette colonne `Month Calendar`en.  
  
 La colonne calculée Month Calendar fournit un nom triable pour le mois.  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a>Créer une colonne calculée de jour de la semaine dans la table Date  
  
1.  Avec la table **Date** encore active, cliquez sur le menu **Colonne** , puis sur **Ajouter une colonne**.  
  
     Une nouvelle colonne est ajoutée à droite de la table.  
  
2.  Dans la barre de formule, tapez la formule suivante :  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
3.  Renommez la colonne `Day of Week`en.  
  
4.  Cliquez sur l’en-tête de colonne et faites glisser la colonne entre les colonnes **Day Name** et **Day of Month** .  
  
    > [!TIP]  
    >  Déplacer les colonnes dans la table facilite la navigation.  
  
 La colonne calculée Day of Week fournit un nom triable pour le jour de la semaine.  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a>Créer une colonne calculée de nom de sous-catégorie de produit dans la table Product  
  
1.  Dans le concepteur de modèles, sélectionnez la table **Product** .  
  
2.  Faites défiler la table sur la droite. Notez que la colonne la plus à droite est nommée **Add Column** (en italique). Cliquez sur l’en-tête de colonne.  
  
3.  Dans la barre de formule, tapez la formule suivante.  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
4.  Renommez la colonne `Product Subcategory Name`en.  
  
 La colonne calculée Product Subcategory Name est utilisée pour créer une hiérarchie dans la table Product, incluant les données de la colonne Product Subcategory Name dans la table Product Subcategory. Les hiérarchies ne peuvent pas couvrir plusieurs tables. Vous allez créer des hiérarchies plus loin, dans la leçon 7.  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a>Créer une colonne calculée de nom de catégorie de produit dans la table Product  
  
1.  Avec la table **Product** encore active, cliquez sur le menu **Colonne** , puis sur **Ajouter une colonne**.  
  
2.  Dans la barre de formule, tapez la formule suivante :  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
3.  Renommez la colonne `Product Category Name`en.  
  
 La colonne calculée Product Category Name est utilisée pour créer une hiérarchie dans la table Product, incluant les données de la colonne Product Category Name dans la table Product Category. Les hiérarchies ne peuvent pas couvrir plusieurs tables.  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a>Créer une colonne calculée de marge dans la table Internet Sales  
  
1.  Dans le concepteur de modèles, sélectionnez la table **Internet Sales** .  
  
2.  Ajoutez une nouvelle colonne.  
  
3.  Dans la barre de formule, tapez la formule suivante :  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
4.  Renommez la colonne `Margin`en.  
  
5.  Faites glisser la colonne entre les colonnes **Sales Amount** et **Tax Amt** .  
  
 La colonne calculée Margin est utilisée pour analyser les marges bénéficiaires pour chaque ligne (produit).  
  
## <a name="next-step"></a>étape suivante  
 Pour continuer cette leçon, passez à la [Leçon 7 : Créer des mesures](lesson-6-create-measures.md).  
  
  
