---
title: Générateur de modèles tabulaires (SSAS tabulaire) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.TOPLEVSEMMODUIENTRY.F1
ms.assetid: 45735c57-2a95-4e45-8994-7242df6c9c5f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7d0fc5ae763542c5f46bdcdb474a71f71250733c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154030"
---
# <a name="tabular-model-designer-ssas-tabular"></a>Générateur de modèles tabulaires (SSAS Tabulaire)
  Le générateur de modèles tabulaires fait partie de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], intégré à Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 2010 ou une version ultérieure, avec les modèles supplémentaires de type de projet spécifiques au développement de solutions de modèles tabulaires professionnelles.  
  
 Sections de cette rubrique :  
  
-   [Avantages](#bkmk_benefits)  
  
-   [Modèles de projet](#bkmk_proj_temp)  
  
-   [Fenêtres et Menus](#bkmk_wind_men)  
  
-   [Intégration de Visual Studio](#bkmk_vsint)  
  
##  <a name="bkmk_benefits"></a> Avantages  
 Lorsque vous installez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], de nouveaux modèles de projet de création de modèles tabulaires sont ajoutés aux types de projet disponibles. Une fois un nouveau projet de modèle tabulaire créé à l'aide de l'un des modèles, vous pouvez commencer à créer un modèle à l'aide des outils et des assistants du générateur de modèles tabulaires.  
  
 Outres de nouveaux modèles et outils permettant de créer des solutions professionnelles de modèles multidimensionnels et tabulaires, l'environnement [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fournit des fonctionnalités de débogage et de cycle de vie de projet qui vous permettent de créer des solutions décisionnelles les plus puissantes possibles pour votre organisation. Pour plus d'informations sur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consultez [Mise en route de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=206389).  
  
##  <a name="bkmk_proj_temp"></a> Modèles de projets  
 Lorsque vous installez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], les modèles de projet de modèles tabulaires suivants sont ajoutés aux types de projets Business Intelligence :  
  
 **Projet tabulaire Analysis Services**  
 Ce modèle peut être utilisé pour créer un projet de modèle tabulaire vide.  
  
 **Importer à partir du serveur (tabulaire)**  
 Ce modèle peut être utilisé pour créer un projet de modèle tabulaire en extrayant les métadonnées d'un modèle tabulaire existant dans Analysis Services.  
  
 **Importer à partir de PowerPivot**  
 Ce modèle est utilisé pour la création d'un projet de modèle tabulaire en extrayant les métadonnées et les données d'un fichier [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] .  
  
> [!NOTE]  
>  Les projets de modèle tabulaire requièrent une instance de serveur Analysis Services en mode tabulaire, localement ou sur le réseau.  
  
##  <a name="bkmk_wind_men"></a> Fenêtres et menus  
 L'environnement de création de modèles tabulaires de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] inclut ce qui suit :  
  
### <a name="designer-window"></a>Fenêtre de concepteur  
 La fenêtre du concepteur permet de créer des modèles tabulaires en fournissant une représentation visuelle du modèle. Lorsque vous ouvrez le fichier Model.bim, le modèle s'ouvre dans la fenêtre du concepteur. Vous pouvez créer un modèle dans la fenêtre du concepteur à l'aide de deux modes d'affichage différents :  
  
 **Vue de données**  
 La vue de données affiche les tables dans un format de grille tabulaire. Vous pouvez également définir des mesures à l'aide de la grille de mesures, qui peut être affichée pour chaque table dans la vue de données uniquement.  
  
 **Vue du diagramme**  
 La vue de diagramme affiche les tables, avec les relations entre celles-ci, dans un format graphique. Les colonnes, les mesures, les hiérarchies et les indicateurs de performance clés peuvent être filtrés, et vous pouvez choisir d'afficher le modèle à l'aide d'une perspective définie.  
  
 La plupart des tâches de création de modèles peuvent être effectuées dans l'une ou l'autre vue.  
  
### <a name="solution-explorer"></a>Explorateur de solutions  
 La fenêtre Explorateur de solutions présente la solution active comme un conteneur logique d'un projet de modèle tabulaire, avec ses éléments associés. Le projet de modèle (.smproj) contient uniquement un objet Références (vide) et le fichier Model.bim. À partir de cette vue, vous pouvez directement ouvrir les éléments de projet pour les modifier et y effectuer d'autres tâches de gestion.  
  
 Les solutions de modèles tabulaires contiennent généralement un seul projet ; toutefois, une solution peut contenir également d'autres projets, par exemple, un projet Integration Services ou Reporting Services. Vous pouvez ajouter plusieurs fichiers à condition qu'ils ne soient pas du même type que les fichiers de projet de modèle tabulaire, et que leur propriété Action de génération ait pour valeur Aucune, ou que la propriété Copier dans le répertoire de sortie soit définie avec la valeur Ne pas copier.  
  
 Pour afficher l'Explorateur de solutions, dans le menu **Affichage** , cliquez sur **Explorateur de solutions**.  
  
### <a name="properties-window"></a>Fenêtre Propriétés  
 La fenêtre Propriétés affiche les propriétés de l'objet sélectionné. Les objets suivants ont des propriétés qui peuvent être affichées et modifiées dans la fenêtre Propriétés :  
  
-   Model.bim  
  
-   Table de charge de travail  
  
-   colonne  
  
-   Measure  
  
 Les propriétés d'un projet affichent uniquement le nom du projet et le dossier du projet dans la fenêtre Propriétés. Les projets contiennent également des paramètres Options de déploiement et Serveur de déploiement supplémentaires que vous pouvez définir à l'aide d'une boîte de dialogue de propriétés modales. Pour afficher ces propriétés, dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.  
  
 Les champs de la fenêtre Propriétés comportent des contrôles intégrés qui s'ouvrent en cliquant dessus. Le type de contrôle d'édition varie selon la propriété. Ces contrôles comprennent des zones d'édition, des listes déroulantes et des liens vers des boîtes de dialogue personnalisées. Les propriétés qui apparaissent en grisé sont en lecture seule.  
  
 Pour afficher la fenêtre **Propriétés** , cliquez sur le menu **Affichage** , puis sur **Fenêtre Propriétés**.  
  
### <a name="error-list"></a>Liste d'erreurs  
 La fenêtre Liste d'erreurs contient des messages concernant l'état du modèle :  
  
-   Notifications concernant les méthodes conseillées pour la sécurité.  
  
-   Impératifs liés au traitement des données.  
  
-   Informations d'erreurs sémantiques pour les colonnes calculées, les mesures et les filtres de lignes pour les rôles. Pour les colonnes calculées, vous pouvez double-cliquer sur le message d'erreur pour accéder à la source de l'erreur.  
  
-   Erreurs de validation DirectQuery.  
  
 Par défaut, **Liste d'erreurs** n'apparaît que lorsqu'une erreur est retournée. Vous pouvez, toutefois, afficher la fenêtre **Liste d'erreurs** à tout moment. Pour afficher la fenêtre **Liste d'erreurs** , cliquez sur le menu **Affichage** , puis sur **Liste d'erreurs**.  
  
### <a name="output"></a>Sortie  
 Les informations de génération et de déploiement sont affichées dans la fenêtre **Sortie** (en plus de la boîte de dialogue modale de progression). Pour afficher la fenêtre **Sortie** , cliquez sur le menu **Affichage** , puis sur Sortie.  
  
### <a name="menu-items"></a>Éléments de menu  
 Lorsque vous installez [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], des éléments de menu supplémentaires spécifiques à la création de modèles tabulaires sont ajoutés à la barre de menus Visual Studio. Le menu **Modèle** peut être utilisé pour lancer l'Assistant Importation de données, voir les connexions existantes, traiter les données d'espace de travail et parcourir l'espace de travail de modèle dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel. Le menu **Table** est utilisé pour créer et gérer des relations entre des tables, créer et gérer des mesures, spécifier des paramètres de table de données, spécifier des options de calcul et spécifier d'autres propriétés de table. Avec le menu **Colonne** , vous pouvez ajouter et supprimer des colonnes dans une table, masquer et afficher des colonnes et spécifier d'autres propriétés de colonne telles que les types de données et les filtres. Vous pouvez générer et déployer des solutions de modèles tabulaires à partir du menu **Génération** . Les fonctions Copier/Coller sont incluses dans le menu **Édition** .  
  
 En plus de ces éléments de menu, des paramètres supplémentaires sont ajoutés aux options Analysis Services accessibles dans les éléments du menu Outils.  
  
### <a name="toolbar"></a>Barre d'outils  
 La barre d'outils Analysis Services fournit un accès rapide et aisé aux commandes de création de modèles utilisées les plus fréquemment.  
  
##  <a name="bkmk_vsint"></a> Intégration à Visual Studio  
 **contrôle de code source ;**  
 Les projets Analysis Services s'intègrent au plug-in sélectionné du contrôle de code source. Si vous avez configuré Visual Studio pour utiliser le contrôle de code source, vous pouvez utiliser l'insertion/l'extraction à partir de l'Explorateur de solutions. Pour configurer l'utilisation de Team Foundation Server, consultez [Configurer Visual Studio avec le contrôle de version de Team Foundation](http://msdn.microsoft.com/library/ms253064.aspx). De nombreux plug-ins de contrôle de code source tiers sont également pris en charge.  
  
 **Polices**  
 Les modèles tabulaires utilisent la police d'environnement [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour contrôler les polices dans l'affichage. Il peut être nécessaire de modifier cette police si la police par défaut de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne dispose pas de tous les caractères Unicode dont vous avez besoin pour votre langage. Pour modifier les polices, cliquez sur le menu **Outils** , puis sur **Options**et sur **Polices et couleurs**.  
  
 **Raccourcis clavier**  
 Les raccourcis clavier Analysis Services peuvent être configurés/remappés via la boîte de dialogue Outils->Options->Clavier. Certains raccourcis globaux de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , permettant notamment la génération, l'enregistrement, le débogage, la création d'un nouveau projet, etc. sont pris en charge dans le contexte du générateur de modèles tabulaires. D'autres raccourcis spécifiques du générateur de modèles tabulaires sont présents dans le contexte d'Analysis Services.  
  
## <a name="see-also"></a>Voir aussi  
 [Projets de modèles tabulaires &#40;SSAS tabulaire&#41;](tabular-models/tabular-model-projects-ssas-tabular.md)   
 [Propriétés &#40;SSAS tabulaire&#41;](tabular-models/properties-ssas-tabular.md)  
  
  