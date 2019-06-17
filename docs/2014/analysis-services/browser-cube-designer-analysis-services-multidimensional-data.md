---
title: Navigateur (Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.view.f1
ms.assetid: efb5ee1c-de50-4bfc-83ff-08a4f03c3ece
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4415fedb492eb32c2929c50999cad1542b41ca78
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66064617"
---
# <a name="browser-cube-designer-analysis-services---multidimensional-data"></a>Navigateur (Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  L’onglet **Navigateur** du Concepteur de cube permet d’explorer les dimensions, les mesures et les indicateurs de performance clés (KPI) d’un cube. Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], le navigateur de cube [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] est intégré au concepteur de requêtes MDX et fournit des interfaces utilisateur graphiques pour vous aider à créer des requêtes MDX, filtrer et découper les cubes et descendre dans les hiérarchies.  
  
 Le **navigateur** onglet comporte deux modes : **Le Mode Création** et **en Mode requête**. Dans chaque mode, vous pouvez utiliser les objets du volet **Métadonnées** pour explorer le cube, ou vous pouvez faire glisser des membres du volet **Métadonnées** vers une zone de requête pour créer une requête MDX qui extraie les données que vous voulez utiliser.  
  
 **Parcourir et interroger à l’aide du Mode de conception graphique**  
  
 L’illustration suivante montre l’interface du **Navigateur** en **mode Création**graphique.  
  
 ![Concepteur de requêtes MDX Analysis Services, mode Création](media/rsqd-dsawas-mdx-designmode.gif "Concepteur de requêtes MDX Analysis Services, mode Création")  
  
 Lorsque vous travaillez en mode de conception graphique, si le **exécution automatique** (![exécuter automatiquement la requête](media/rsqdicon-autoexecute.gif "exécuter automatiquement la requête")) activer/désactiver la barre d’outils est sélectionnée, le **Navigateur** exécute une requête chaque fois que vous déposez un objet de métadonnées dans le volet des données. Vous pouvez aussi exécuter manuellement la requête à l’aide de la **exécuter la requête** (![exécuter la requête](media/rsqdicon-run.gif "exécuter la requête")) dans la barre d’outils.  
  
 Pour faire passer le concepteur de requêtes graphique en mode **Requête** et travailler avec le texte des instructions MDX, cliquez sur le bouton correspondant au **mode Création** dans la barre d’outils.  
  
 **Parcourir et interroger à l’aide du Mode texte MDX**  
  
 Lorsque vous êtes en mode de création de texte MDX, vous pouvez utiliser directement MDX. Le volet **Métadonnées** reste disponible, ce qui vous permet d’ajouter des objets à la zone de création de requête et glisser-déplacer des fonctions et des opérateurs MDX à partir de la liste du volet **Fonctions** .  
  
 L’illustration suivante montre l’interface du **Navigateur** pour le mode Requête.  
  
 ![Concepteur de requêtes MDX Analysis Services, mode Requête](media/rsqd-dsawas-mdx-querymode.gif "Concepteur de requêtes MDX Analysis Services, mode Requête")  
  
 Vous pouvez commencer à travailler en mode de création graphique, ajouter tous les objets requis, ajouter des filtres pour découper le cube, puis basculer en mode texte pour étendre la requête MDX générée par défaut et pour inclure des propriétés de membre et de cellule supplémentaires.  
  
 Le volet **Métadonnées** affiche les onglets **Métadonnées** et **Fonctions**. À partir de l’onglet **Métadonnées** , vous pouvez faire glisser des dimensions, des hiérarchies, des indicateurs de performance clés (KPI) et des mesures vers la zone de création de requêtes. Vous pouvez faire glisser des fonctions de l’onglet **Fonctions** vers la zone de création de requêtes. Lorsque vous exécutez la requête, la zone de création des requêtes affiche les résultats de la requête MDX. Vous pouvez aussi cliquer sur **Analyser dans Excel** dans la **Barre d’outils** pour exporter les données vers Microsoft Office Excel et afficher les résultats tels que les utilisateurs peuvent les voir. Les sections suivantes décrivent plus en détail la barre d’outils et tous les volets de chaque mode du **Navigateur** .  
  
 Notez que, lorsque vous travaillez en mode texte, le **exécution automatique** (![exécuter automatiquement la requête](media/rsqdicon-autoexecute.gif "exécuter automatiquement la requête")) activer/désactiver la barre d’outils n’est pas disponible. Toutefois, vous pouvez exécuter manuellement des requêtes à l’aide de la **exécuter la requête** (![exécuter la requête](media/rsqdicon-run.gif "exécuter la requête")) dans la barre d’outils.  
  
## <a name="sections"></a>Sections  
 **Barre d'outils**  
 La barre d'outils contient les outils qui peuvent être utilisés dans les vues du mode Création ou du mode Requête. Pour plus d’informations sur la barre d’outils et sur l’utilisation de ces fonctionnalités, consultez [Barre d’outils &#40;onglet Navigateur, Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md).  
  
 **Analyser dans Excel**  
 La fonctionnalité **Analyser dans Excel** permet d’envoyer la sélection actuelle de données du cube vers Excel et ainsi d’afficher un aperçu des données dans un tableau croisé dynamique. La sélection de données actuelle dépend des éléments que vous avez ajoutés à partir du volet **Métadonnées** et des filtres que vous avez éventuellement définis à l’aide des fonctions de création de filtre et de requête. Pour plus d’informations, consultez [Analyser dans Excel &#40;onglet Explorateur, Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md).  
  
 **Métadonnées**  
 Le volet **Métadonnées** permet d’afficher les objets contenus dans un cube, d’explorer les hiérarchies et d’examiner et utiliser les mesures. Après avoir sélectionné les données, vous pouvez afficher les données associées dans le volet **Rapport**. Pour plus d’informations sur ce volet, consultez [Métadonnées &#40;onglet Navigateur, Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md).  
  
 **Filtre et requête**  
 Cette zone de l’aire de conception permet de générer des requêtes MDX en faisant glisser des objets à partir du volet **Métadonnées** et en spécifiant des critères de filtre sur le cube ou la dimension source. Pour plus d’informations, consultez [Interroger et filtrer &#40;onglet Navigateur, Concepteur de cube&#41; &#40;Analysis Services - Données multidimensionnelles&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Objets de cube &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)   
 [Cubes dans les modèles multidimensionnels](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)  
  
  
