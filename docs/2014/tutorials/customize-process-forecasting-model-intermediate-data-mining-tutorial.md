---
title: Personnalisation et traitement du modèle de prévision (Didacticiel intermédiaire sur l’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4bd25e15-9d9e-4528-b7bc-ccb856643aec
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d2d0e73d1d9a4058ff63320552604b2bfa1bca8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63249401"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a>Personnalisation et traitement du modèle de prévision (Didacticiel sur l'exploration de données intermédiaire)
  L'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)]) fournit des paramètres qui affectent la façon dont un modèle est créé et la façon dont les données chronologiques sont analysées. La modification de ces propriétés peuvent affecter de manière importante la manière dont le modèle d'exploration de données élabore des prédictions.  
  
 Pour cette tâche du didacticiel, vous effectuerez les tâches suivantes pour modifier le modèle :  
  
1.  Vous allez personnaliser la manière dont votre modèle gère les périodes en ajoutant une nouvelle valeur pour le paramètre *PERIODICITY_HINT* .  
  
2.  Vous découvrirez deux autres paramètres importants pour l'algorithme MTS : FORECAST_METHOD qui vous permet de contrôler la méthode utilisée pour les prédictions, et PREDICTION_SMOOTHING, qui vous permet de personnaliser le mélange des prédictions à long terme et à court terme.  
  
3.  Vous pouvez également dire à l'algorithme la manière dont vous souhaitez imputer les valeurs manquantes.  
  
4.  Après avoir apporté toutes les modifications, vous allez déployer et traiter le modèle.  
  
## <a name="setting-time-series-parameters"></a>Définition des paramètres de série chronologique  
 **Indications de périodicité**  
  
 Le paramètre *PERIODICITY_HINT* fournit à l’algorithme des informations sur les périodes supplémentaires que vous vous attendez à voir dans les données. Par défaut, les modèles de série chronologique essayeront de détecter automatiquement un modèle dans les données. Toutefois, si vous connaissez déjà le cycle de temps estimé, fournir un indicateur de périodicité peut potentiellement améliorer la précision du modèle. Toutefois, si vous fournissez le mauvais indicateur de périodicité, celui-ci peut diminuer la précision ; par conséquent, si vous ne savez pas précisément quelle valeur doit être utilisée, il est préférable d'utiliser la valeur par défaut.  
  
 Par exemple, la vue utilisée pour ce modèle regroupe les données de ventes [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] mensuellement. Par conséquent, chaque tranche de temps utilisée par le modèle représente un mois et toutes les prédictions se feront également en termes de mois. Étant donné qu’il y a 12 mois dans une année et que vous vous attendez à ce que les modèles de vente se répètent plus ** ou moins sur `12`une base annuelle, vous définissez le paramètre PERIODICITY_HINT sur, pour indiquer que 12 tranches de temps (mois) constituent un cycle de vente complet.  
  
 **Méthode de prévisions**  
  
 Le paramètre *FORECAST_METHOD* contrôle si l’algorithme MTS (Time Series) est optimisé pour les prédictions à long terme ou à long terme. Par défaut, le paramètre *FORECAST_METHOD* est défini sur Mixed, ce qui signifie que deux algorithmes différents sont fusionnés et équilibrés pour fournir de bons résultats pour la prédiction à long terme et à long terme.  
  
 Toutefois, si vous savez que vous souhaitez utiliser un algorithme particulier, vous pouvez modifier la valeur sur ARIMA ou ARTXP.  
  
 **Pondération des prédictions à long terme et à long terme**  
  
 Vous pouvez également personnaliser la manière dont les prédictions à long terme et à court terme sont combinées à l'aide du paramètre PREDICTION_SMOOTHING. Par défaut, ce paramètre est défini sur 0,5, ce qui fournit généralement le meilleur équilibre pour une précision globale.  
  
#### <a name="to-change-the-algorithm-parameters"></a>Pour changer les paramètres d'algorithme  
  
1.  Sous l’onglet **modèles d’exploration de données** , cliquez avec le bouton droit sur **prévisions**, puis sélectionnez définir les **paramètres d’algorithme**.  
  
2.  Dans la `PERIODICITY_HINT` ligne de la boîte de dialogue **paramètres d’algorithme** , cliquez sur la colonne `{12}` **valeur** , puis tapez, y compris les accolades.  
  
     Par défaut, l'algorithme ajoute également la valeur {1}.  
  
3.  Dans la `FORECAST_METHOD` ligne, vérifiez que la zone de texte **valeur** est vide ou a la `MIXED`valeur. Si une valeur différente a été entrée, tapez `MIXED` pour rétablir la valeur par défaut du paramètre.  
  
4.  Dans la ligne **PREDICTION_SMOOTHING** , vérifiez que la zone de texte **valeur** est vide ou définie sur 0,5. Si une valeur différente a été entrée, cliquez sur **valeur** et `0.5` tapez pour rétablir la valeur par défaut du paramètre.  
  
    > [!NOTE]  
    >  Le paramètre PREDICTION_SMOOTHING est uniquement disponible dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise. Par conséquent, vous ne pouvez ni afficher ni modifier la valeur du paramètre PREDICTION_SMOOTHING dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard. Toutefois, le comportement par défaut consiste à utiliser les deux algorithmes et à les pondérer de manière égale.  
  
5.  Cliquez sur **OK**.  
  
## <a name="handling-missing-data-optional"></a>Gestion des données manquantes (facultatif)  
 Dans de nombreux cas, vos données de ventes peuvent comporter des vides comblés par des valeurs NULL, ou un magasin peut ne pas avoir respecté la date limite du signalement des données, ce qui laisse une cellule vide à la fin d'une série. Dans de tels scénarios, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] déclenche l'erreur suivante et ne traite pas le modèle.  
  
 «Erreur (exploration de données) : horodatages non synchronisés à partir \<du nom de série de série>, du \<modèle d’exploration de données, nom de modèle>. Toutes les séries chronologiques doivent se terminer à la même marque de temps et ne peuvent pas comporter des points de données arbitrairement absents. L'attribution de la valeur Previous ou de la valeur d'une constante numérique au paramètre MISSING_VALUE_SUBSTITUTION fournit automatiquement les points de données absents lorsque cela est possible. »  
  
 Pour éviter cette erreur, vous pouvez spécifier [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] doit automatiquement fournir de nouvelles valeurs pour remplir les écarts à l'aide d'une des méthodes suivantes :  
  
-   Utilisation d'une valeur moyenne. La moyenne est calculée à l'aide de toutes les valeurs valides comprises dans la même série de données.  
  
-   Utilisation de la valeur précédente. Vous pouvez substituer des valeurs précédentes à plusieurs cellules manquantes, mais vous ne pouvez pas remplir les valeurs de début.  
  
-   Utilisation d'une valeur constante que vous fournissez.  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a>Pour spécifier le remplissage des vides par des valeurs moyennes  
  
1.  Sous l’onglet **modèles d’exploration de données** , cliquez avec le bouton droit sur la colonne **prévision** , puis sélectionnez définir les paramètres de l' **algorithme**.  
  
2.  Dans la boîte de dialogue **paramètres d’algorithme** , dans la ligne **MISSING_VALUE_SUBSTITUTION** , cliquez sur la colonne `Mean` **valeur** , puis tapez.  
  
## <a name="build-the-model"></a>Générer le modèle  
 Pour utiliser le modèle, vous devez le déployer sur un serveur et traiter le modèle en exécutant les données d'apprentissage par l'algorithme.  
  
#### <a name="to-process-the-forecasting-model"></a>Pour traiter le modèle de prévision  
  
1.  Dans le menu **Modèle d'exploration de données** de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], sélectionnez **Traiter l'exploration de données et tous les modèles**.  
  
2.  Cliquez sur **Oui**pour répondre à l'avertissement qui vous invite à indiquer si vous souhaitez générer et déployer le projet.  
  
3.  Dans la boîte de dialogue **traiter la structure d’exploration de données-prévision** , cliquez sur **exécuter**.  
  
     La boîte de dialogue **État d'avancement du traitement** s'affiche et présente les informations relatives au traitement du modèle. Le traitement du modèle peut nécessiter quelques minutes.  
  
4.  Une fois le traitement terminé, cliquez sur **Fermer** pour quitter la boîte de dialogue **État d'avancement du traitement** .  
  
5.  Cliquez à nouveau sur **Fermer** pour quitter la boîte de dialogue **traiter la structure d’exploration de données-prévision** .  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du modèle de prévision &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Référence technique de l’algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Exigences et considérations relatives au traitement &#40;l’exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
