---
title: 'Leçon 5 : mise en forme d’un rapport (Reporting Services) | Microsoft Docs'
description: Découvrez comment mettre en forme les champs de date et de devise, et les en-têtes de colonne, après avoir ajouté une région de données et quelques champs au rapport Sales Orders.
ms.date: 04/29/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ef2d3fd220aef7a593a2244cf2d7509c5264fcca
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245108"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a>Leçon 5 : Mettre en forme un rapport (Reporting Services)

Maintenant que vous avez ajouté une région de données et quelques champs au rapport Sales Orders, vous pouvez mettre en forme les champs de date et de valeurs monétaires, ainsi que les en-têtes de colonne.

## <a name="format-the-date"></a><a name="bkmk_format_date"></a>Mise en forme de la date

L’expression de champ Date affiche les informations de date et d’heure par défaut. Vous pouvez le mettre en forme de sorte qu'il n'affiche que la date.

1. Sélectionnez l’onglet **Conception**.
2. Cliquez avec le bouton droit dans la cellule qui contient l’expression de champ `[Date]`, puis sélectionnez **Propriétés de la zone de texte**.
3. Sélectionnez **Nombre** puis, dans le champ **Catégorie**, sélectionnez **Date**.
4. Dans la zone **Type** , sélectionnez **January 31, 2000**.
5. Sélectionnez **OK** pour appliquer le format.
6. Affichez un aperçu du rapport pour voir la modification apportée à la mise en forme du champ `[Date]`, puis repassez en mode Conception.

## <a name="format-the-currency"></a><a name="bkmk_format_currency"></a>Mise en forme des valeurs monétaires

L’expression de champ LineTotal affiche un nombre général. Vous pouvez appliquer une mise en forme pour afficher ce nombre dans un format monétaire.

1. Cliquez avec le bouton droit dans la cellule qui contient l’expression `[LineTotal]`, puis sélectionnez **Propriétés de la zone de texte**.
2. Sélectionnez **Nombre** dans la zone de liste de la colonne la plus à gauche, et **Devise** dans la zone de liste **Catégorie**.
3. Si votre paramètre régional est Anglais (États-Unis), les valeurs par défaut de la zone de liste **Type** doivent être :
    - **Nombre de décimales : 2**
    - **Nombres négatifs : ($12345.00)**
    - **Symbole : $ Anglais (États-Unis)**
4. Sélectionnez **Utiliser le séparateur de milliers (,)** . Si l’exemple de texte affiché est **$12,345.00**, vos paramètres sont corrects.
5. Sélectionnez **OK** pour appliquer le format.
6. Affichez un aperçu du rapport pour voir la modification apportée à la colonne d’expression `[LineTotal]`, puis repassez en mode Conception.  

## <a name="change-text-style-and-column-widths"></a><a name="bkmk_change_textstyle"></a>Modification du style du texte et de la largeur des colonnes

Vous pouvez ajouter d’autres mises en forme à votre rapport en mettant en surbrillance la ligne d’en-tête et en ajustant la largeur des colonnes de données.

### <a name="to-format-header-rows-and-table-columns"></a>Pour mettre en forme les lignes d'en-tête et les colonnes de la table

1. Sélectionnez la table pour que les poignées de ligne et de colonne apparaissent au-dessus et à côté de la table. Les barres grises le long du haut et du côté de la table sont les poignées de colonne et de ligne.

2. Placez le curseur entre les séparateurs de colonne pour qu'il se transforme en flèche à deux pointes. Faites glisser les colonnes pour les redimensionner.
    ![rs_BasicTableDetailsDesign](media/rs-basictabledetailsdesign.png)

3. Sélectionnez la ligne qui contient les étiquettes d’en-tête de colonne et, dans le menu **Format**, sélectionnez **Police** > **Gras**.

4. Affichez un aperçu de votre rapport. Il doit ressembler à ceci :

    ![Aperçu de table avec en-têtes de colonnes en gras](media/rs-basictabledetailsformattedpreview.png "Aperçu de table avec en-têtes de colonnes en gras")  

5. Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le rapport.

## <a name="next-steps"></a>Étapes suivantes

Dans cette leçon, vous avez mis en forme des en-têtes de colonnes et des expressions de champs. Maintenant, vous allez ajouter un regroupement et des totaux à votre rapport. Passez à la [Leçon 6 : Ajouter un regroupement et des totaux &#40;Reporting Services&#41;](lesson-6-adding-grouping-and-totals-reporting-services.md).

## <a name="see-also"></a>Voir aussi

[Mise en forme des nombres et des dates &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)
[Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](report-design/rendering-behaviors-report-builder-and-ssrs.md)
