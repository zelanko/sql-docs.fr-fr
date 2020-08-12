---
title: Ajouter une moyenne mobile à un graphique (Générateur de rapports) | Microsoft Docs
description: Découvrez comment l’indicateur de prix de formule de moyenne mobile peut être affiché sur un graphique pour identifier les tendances dans le Générateur de rapports.
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b2c72f3720b397e20df7daa794e08ef7ca241abf
ms.sourcegitcommit: 93e4fd75e8fe0cc85e7949c9adf23b0e1c275465
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84255698"
---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a>Ajouter une moyenne mobile à un graphique (Générateur de rapports et SSRS)
Une moyenne mobile est une moyenne des données de votre série, calculée sur une période de temps définie. Dans des rapports paginés [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , la moyenne mobile peut être indiquée sur le graphique pour identifier des tendances significatives.  

![didacticiel-histogramme-générateur-de-rapports](../../reporting-services/media/report-builder-column-chart-tutorial.png)
  
 La formule de moyenne mobile est l'indicateur de prix le plus populaire utilisé dans les analyses techniques. De nombreuses autres formules, y compris la moyenne, la médiane et l'écart type, peuvent également être dérivées d'une série sur le graphique. Lors de la spécification d'une moyenne mobile, chaque formule peut comporter un ou plusieurs paramètres qui doivent être spécifiés.  
 
 Le [Didacticiel : ajouter un histogramme à un rapport (Générateur de rapports)](../tutorial-add-a-column-chart-to-your-report-report-builder.md) vous guide pas à pas dans la procédure d’ajout d’une moyenne mobile à un graphique, si vous voulez essayer avec des exemples de données.
  
 Lorsqu'une formule de moyenne mobile est ajoutée en mode Création, la série de lignes ajoutée est uniquement un espace réservé visuel. Le graphique calculera les points de données de chaque formule pendant le traitement des rapports.  
  
 La prise en charge intégrée des courbes de tendance n’est pas disponible dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a>Pour ajouter une moyenne mobile calculée à une série sur le graphique  
  
1.  Cliquez avec le bouton droit sur un champ dans la zone **Valeurs** , puis cliquez sur **Ajouter une série calculée**. La boîte de dialogue **Propriétés de la série calculée** s'ouvre.  
  
2.  Sélectionnez l’option **Moyenne mobile** dans la liste déroulante **Formule** .  
  
3.  Spécifiez une valeur entière pour la **Période** qui représente la période de la moyenne mobile.  
  
    > [!NOTE]  
    >  La période est le nombre de jours utilisés pour calculer une moyenne mobile. Si les valeurs de date/d'heure ne sont pas spécifiées sur l'axe des abscisses, la période est représentée par le nombre de points de données utilisés pour calculer une moyenne mobile. S'il n'existe qu'un seul point de données, la formule de moyenne mobile n'effectue pas de calcul. La moyenne mobile est calculée en commençant par le deuxième point. Si vous spécifiez l'option **Démarrer à partir du premier point** , le graphique démarrera la moyenne mobile au niveau du premier point. S'il n'existe qu'un seul point de données, le point dans la moyenne mobile calculée sera identique au premier point dans votre série d'origine.  
  
## <a name="see-also"></a>Voir aussi  
* [Tutoriel : Ajouter un histogramme à un rapport (Générateur de rapports)](../tutorial-add-a-column-chart-to-your-report-report-builder.md)
*  [Mise en forme d’un graphique (Générateur de rapports et SSRS)](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
*  [Graphiques (Générateur de rapports et SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
*  [Ajouter des points vides à un graphique (Générateur de rapports et SSRS)](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
