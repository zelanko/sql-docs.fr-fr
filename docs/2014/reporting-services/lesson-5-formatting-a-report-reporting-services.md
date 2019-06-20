---
title: 'Leçon 5 : Mettre en forme un rapport (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f1acd7bf033ca2170a2a2b0cb1f701606510bf14
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108430"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a>Leçon 5 : Mettre en forme un rapport (Reporting Services)
  Maintenant que vous avez ajouté une région de données et quelques champs au rapport Sales Orders, vous pouvez mettre en forme les champs de date et de valeurs monétaires, ainsi que les en-têtes de colonne.  
  
 Dans cette rubrique :  
  
-   [Mettre en forme la Date](#bkmk_format_date)  
  
-   [Mettre en forme la devise](#bkmk_format_currency)  
  
-   [Modification du Style de texte et des largeurs de colonne](#bkmk_change_textstyle)  
  
##  <a name="bkmk_format_date"></a> Mettre en forme la Date  
 Le champ Date affiche les informations de date et d'heure par défaut. Vous pouvez le mettre en forme de sorte qu'il n'affiche que la date.  
  
#### <a name="to-format-a-date-field"></a>Pour appliquer un format de date  
  
1.  Cliquez sur l'onglet **Conception** .  
  
2.  Cliquez avec le bouton droit sur la cellule qui contient l’expression de champ `[Date]` , puis cliquez sur **Propriétés de la zone de texte**.  
  
3.  Cliquez sur **nombre**, puis, dans le **catégorie** champ, sélectionnez `Date`.  
  
4.  Dans la zone **Type** , sélectionnez **January 31, 2000**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Affichez un aperçu du rapport pour voir la modification apportée au champ `[Date]` , puis repassez en mode Conception.  
  
##  <a name="bkmk_format_currency"></a> Mettre en forme la devise  
 Le champ LineTotal affiche un nombre général. Appliquez une mise en forme pour afficher ce nombre dans un format monétaire.  
  
#### <a name="to-format-a-currency-field"></a>Pour mettre en forme un champ monétaire  
  
1.  Cliquez avec le bouton droit sur la cellule qui contient l'expression de champ `[LineTotal]` , puis sélectionnez **Propriétés de la zone de texte**.  
  
2.  Cliquez sur **Nombre**puis, dans le champ **Catégorie** , sélectionnez **Devise**.  
  
3.  Si votre paramètre régional est Anglais (États-Unis), les valeurs par défaut doivent être :  
  
    -   **Nombre de décimales : 2**  
  
    -   **Nombres négatifs : ($12345.00)**  
  
    -   **Symbole : $ Anglais (États-Unis)**  
  
4.  Sélectionnez **Utiliser le séparateur de milliers (,)**.  
  
     Si l'exemple de texte est :**$12,345.00**, vos paramètres sont corrects.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Affichez un aperçu du rapport pour voir la modification apportée au champ `[LineTotal]` , puis repassez en mode Conception.  
  
##  <a name="bkmk_change_textstyle"></a> Modification du Style de texte et des largeurs de colonne  
 Vous pouvez également modifier la mise en forme de la ligne d'en-tête afin de la différencier des lignes de données du rapport. Enfin, vous pouvez ajuster les largeurs de colonnes.  
  
#### <a name="to-format-header-rows-and-table-columns"></a>Pour mettre en forme les lignes d'en-tête et les colonnes de la table  
  
1.  Cliquez sur la table pour que les poignées de ligne et de colonne apparaissent au-dessus et à côté de la table.  
  
     ![Conception, Table avec ligne d’en-tête et de ligne de détails](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "conception, Table avec ligne d’en-tête et de ligne de détails")  
  
     Les barres grises le long du haut et du côté de la table sont les poignées de colonne et de ligne.  
  
2.  Placez le curseur entre les séparateurs de colonne pour qu'il se transforme en flèche à deux pointes. Faites glisser les colonnes pour les redimensionner.  
  
3.  Sélectionnez la ligne qui contient les étiquettes d'en-tête de colonne et, dans le menu **Format** , pointez sur **Police** , puis cliquez **Gras**.  
  
4.  Cliquez sur l'onglet **Aperçu** pour afficher un aperçu du rapport. Il doit se présenter comme suit :  
  
     ![Aperçu de table avec en-têtes de colonnes en gras](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "Aperçu de table avec en-têtes de colonnes en gras")  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout** pour enregistrer le rapport.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez correctement mis en forme les en-têtes de colonne, ainsi que les valeurs de date et valeurs monétaires. Vous allez ensuite ajouter un regroupement et des totaux à votre rapport. Voir [Leçon 6 : Ajouter un regroupement et des totaux &#40;Reporting Services&#41;](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des nombres et des dates &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
