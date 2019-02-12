---
title: Personnalisation et traitement du modèle de prévision (didacticiel d’exploration de données intermédiaire) | Microsoft Docs
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
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031680"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a>Personnalisation et traitement du modèle de prévision (Didacticiel sur l'exploration de données intermédiaire)
  L'algorithme MTS ([!INCLUDE[msCoName](../includes/msconame-md.md)]) fournit des paramètres qui affectent la façon dont un modèle est créé et la façon dont les données chronologiques sont analysées. La modification de ces propriétés peuvent affecter de manière importante la manière dont le modèle d'exploration de données élabore des prédictions.  
  
 Pour cette tâche du didacticiel, vous effectuerez les tâches suivantes pour modifier le modèle :  
  
1.  Vous allez personnaliser la manière dont votre modèle gère les périodes de temps en ajoutant une nouvelle valeur pour le *PERIODICITY_HINT* paramètre.  
  
2.  Vous allez découvrir deux autres paramètres importants pour l’algorithme Microsoft Time Series : FORECAST_METHOD, ce qui vous permet de contrôler la méthode utilisée pour la prévision, et PREDICTION_SMOOTHING, qui vous permet de personnaliser le mélange des prédictions à court terme et à long terme.  
  
3.  Vous pouvez également dire à l'algorithme la manière dont vous souhaitez imputer les valeurs manquantes.  
  
4.  Après avoir apporté toutes les modifications, vous allez déployer et traiter le modèle.  
  
## <a name="setting-time-series-parameters"></a>Définition des paramètres de série chronologique  
 **Indications de périodicité**  
  
 Le *PERIODICITY_HINT* paramètre fournit l’algorithme des informations sur les périodes supplémentaires que vous souhaitez voir dans les données. Par défaut, les modèles de série chronologique essayeront de détecter automatiquement un modèle dans les données. Toutefois, si vous connaissez déjà le cycle de temps estimé, fournir un indicateur de périodicité peut potentiellement améliorer la précision du modèle. Toutefois, si vous fournissez le mauvais indicateur de périodicité, celui-ci peut diminuer la précision ; par conséquent, si vous ne savez pas précisément quelle valeur doit être utilisée, il est préférable d'utiliser la valeur par défaut.  
  
 Par exemple, la vue utilisée pour ce modèle regroupe les données de ventes [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] mensuellement. Par conséquent, chaque tranche de temps utilisée par le modèle représente un mois et toutes les prédictions se feront également en termes de mois. Dans la mesure où il existe 12 mois dans une année et vous attendez que les modèles de ventes plus ou moins répéter sur une base annuelle, vous allez définir la *PERIODICITY_HINT* paramètre `12`pour indiquer que 12 tranches de temps (mois) constituent une cycle de ventes complet.  
  
 **Prévision (méthode)**  
  
 Le *FORECAST_METHOD* paramètre contrôle si l’algorithme de série chronologique est optimisé pour les prédictions à court terme ou à long terme. Par défaut, le *FORECAST_METHOD* paramètre est défini sur MIXED, ce qui signifie que les deux algorithmes différents sont fusionnés et équilibrés pour fournir de bons résultats pour la prédiction à court terme et à long terme.  
  
 Toutefois, si vous savez que vous souhaitez utiliser un algorithme particulier, vous pouvez modifier la valeur sur ARIMA ou ARTXP.  
  
 **Pondération de vs à long terme. Prédictions à court terme**  
  
 Vous pouvez également personnaliser la manière dont les prédictions à long terme et à court terme sont combinées à l'aide du paramètre PREDICTION_SMOOTHING. Par défaut, ce paramètre est défini sur 0,5, ce qui fournit généralement le meilleur équilibre pour une précision globale.  
  
#### <a name="to-change-the-algorithm-parameters"></a>Pour changer les paramètres d'algorithme  
  
1.  Sur le **des modèles d’exploration de données** droit **Forecasting**et sélectionnez **paramètres d’algorithme définir**.  
  
2.  Dans le `PERIODICITY_HINT` ligne de la **paramètres d’algorithme** boîte de dialogue, cliquez sur le **valeur** colonne, puis tapez `{12}`, y compris les accolades.  
  
     Par défaut, l'algorithme ajoute également la valeur {1}.  
  
3.  Dans le `FORECAST_METHOD` de ligne, vérifiez que le **valeur** zone de texte est vide ou définie à `MIXED`. Si une valeur différente a été entrée, tapez `MIXED` pour le paramètre de rétablir la valeur par défaut.  
  
4.  Dans le **PREDICTION_SMOOTHING** de ligne, vérifiez que le **valeur** zone de texte est vide ou définie sur 0,5. Si une valeur différente a été entrée, cliquez sur **valeur** et type `0.5` pour le paramètre de rétablir la valeur par défaut.  
  
    > [!NOTE]  
    >  Le paramètre PREDICTION_SMOOTHING est uniquement disponible dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise. Par conséquent, vous ne pouvez ni afficher ni modifier la valeur du paramètre PREDICTION_SMOOTHING dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard. Toutefois, le comportement par défaut consiste à utiliser les deux algorithmes et à les pondérer de manière égale.  
  
5.  Cliquez sur **OK**.  
  
## <a name="handling-missing-data-optional"></a>Gestion des données manquantes (facultatif)  
 Dans de nombreux cas, vos données de ventes peuvent comporter des vides comblés par des valeurs NULL, ou un magasin peut ne pas avoir respecté la date limite du signalement des données, ce qui laisse une cellule vide à la fin d'une série. Dans de tels scénarios, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] déclenche l'erreur suivante et ne traite pas le modèle.  
  
 « Erreur (exploration de données) : Horodatages non synchronisés en commençant par série \<nom de la série >, du modèle d’exploration de données, \<nom_modèle >. Toutes les séries chronologiques doivent se terminer à la même marque de temps et ne peuvent pas comporter des points de données arbitrairement absents. L'attribution de la valeur Previous ou de la valeur d'une constante numérique au paramètre MISSING_VALUE_SUBSTITUTION fournit automatiquement les points de données absents lorsque cela est possible. »  
  
 Pour éviter cette erreur, vous pouvez spécifier [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] doit automatiquement fournir de nouvelles valeurs pour remplir les écarts à l'aide d'une des méthodes suivantes :  
  
-   Utilisation d'une valeur moyenne. La moyenne est calculée à l'aide de toutes les valeurs valides comprises dans la même série de données.  
  
-   Utilisation de la valeur précédente. Vous pouvez substituer des valeurs précédentes à plusieurs cellules manquantes, mais vous ne pouvez pas remplir les valeurs de début.  
  
-   Utilisation d'une valeur constante que vous fournissez.  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a>Pour spécifier le remplissage des vides par des valeurs moyennes  
  
1.  Sur le **des modèles d’exploration de données** onglet, cliquez sur le **Forecasting** colonne, puis sélectionnez **paramètres d’algorithme définir**.  
  
2.  Dans le **paramètres d’algorithme** boîte de dialogue le **MISSING_VALUE_SUBSTITUTION** de ligne, cliquez sur le **valeur** colonne et tapez `Mean`.  
  
## <a name="build-the-model"></a>Générer le modèle  
 Pour utiliser le modèle, vous devez le déployer sur un serveur et traiter le modèle en exécutant les données d'apprentissage par l'algorithme.  
  
#### <a name="to-process-the-forecasting-model"></a>Pour traiter le modèle de prévision  
  
1.  Dans le menu **Modèle d'exploration de données** de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], sélectionnez **Traiter l'exploration de données et tous les modèles**.  
  
2.  Cliquez sur **Oui**pour répondre à l'avertissement qui vous invite à indiquer si vous souhaitez générer et déployer le projet.  
  
3.  Dans le **traiter la Structure d’exploration de données - prévision** boîte de dialogue, cliquez sur **exécuter**.  
  
     La boîte de dialogue **État d'avancement du traitement** s'affiche et présente les informations relatives au traitement du modèle. Le traitement du modèle peut nécessiter quelques minutes.  
  
4.  Une fois le traitement terminé, cliquez sur **Fermer** pour quitter la boîte de dialogue **État d'avancement du traitement** .  
  
5.  Cliquez sur **fermer** pour quitter le **traiter la Structure d’exploration de données - prévision** boîte de dialogue.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Exploration du modèle de prévision &#40;didacticiel d’exploration de données intermédiaire&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Références techniques relatives à l'algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Algorithme MTS (Microsoft Time Series)](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Exigences et considérations concernant le traitement &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
