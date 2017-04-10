---
title: "Le&#231;on&#160;14&#160;: D&#233;ploiement | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on&#160;14&#160;: D&#233;ploiement
Dans cette leçon, vous allez configurer les propriétés de déploiement ; pour cela, vous allez spécifier une instance de serveur de déploiement d'Analysis Services qui s'exécute en mode tabulaire, ainsi qu'un nom pour le modèle que vous déployez. Vous allez ensuite déployer le modèle sur cette instance. Après son déploiement, les utilisateurs peuvent se connecter au modèle en utilisant une application de création de rapports cliente. Pour plus d’informations, consultez [Déploiement d’une solution de modèle tabulaire &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
Durée estimée pour effectuer cette leçon : **5 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 13 : Analyser dans Excel](../analysis-services/lesson-13-analyze-in-excel.md).  
  
## Déployer le modèle  
  
#### Pour configurer les propriétés de déploiement  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Adventure Works Internet Sales Tabular Model**, puis dans le menu contextuel, cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Pages des propriétés de AW Internet Sales Tabular Model**, sous **Serveur de déploiement**, dans la propriété **Serveur**, tapez le nom d’une instance Analysis Services en mode tabulaire. Ce sera l'instance sur laquelle sera déployé votre modèle.  
  
    > [!IMPORTANT]  
    > Vous devez disposer d'autorisations d'administration sur une instance Analysis Services distante afin de déployer dans celle-ci.  
  
3.  Dans la propriété **Base de données**, tapez **Adventure Works Internet Sales Model**.  
  
4.  Dans la propriété Name de **Cube**, tapez **Adventure Works Internet Sales Model**.  
  
5.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
#### Pour déployer le modèle tabulaire Internet Sales Adventure Works  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Générer**, puis cliquez sur **Déployer AW Internet Sales Tabular Model**.  
  
    La boîte de dialogue Déployer apparaît et affiche l'état de déploiement des métadonnées ainsi que de chaque table incluse dans le modèle.  
  
2. Une fois le déploiement correctement effectué, cliquez sur **Fermer**.  
  
## Conclusion  
Félicitations ! Vous avez terminé de créer et déployer votre premier modèle tabulaire Analysis Services. Ce didacticiel vous a guidés dans les tâches courantes pour créer un modèle tabulaire. Maintenant que votre modèle Internet Sales Adventure Works est déployé, vous pouvez utiliser SQL Server Management Studio pour gérer le modèle, créer des scripts de processus et un plan de sauvegarde. Les utilisateurs peuvent se connecter au modèle à l'aide d'une application cliente de création de rapports telle que Microsoft Excel ou [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)].  
  
## Ressources supplémentaires  
Pour en savoir plus sur les propriétés de modèle tabulaire qui prennent en charge les rapports [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], consultez [Propriétés de la génération de rapports Power View &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md).  
  
## Voir aussi  
[Mode DirectQuery &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[Configurer les propriétés par défaut de modélisation des données et de déploiement &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Bases de données model tabulaires #40;SSAS Tabulaire#41;](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  
