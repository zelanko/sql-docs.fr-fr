---
title: Didacticiel DMX sur le panier de marché | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- market basket analysis [Analysis Services]
- tutorials [Data Mining]
- tutorials [DMX]
ms.assetid: 6e262a1d-c89e-4033-8368-46cf25168ef5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe12f1c4ca1c0946572c61e89f4f4edb8ba9a762
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63185642"
---
# <a name="market-basket-dmx-tutorial"></a>Didacticiel DMX Market Basket
  Dans ce didacticiel, vous allez apprendre à créer et explorer des modèles d'exploration de données, ou à en effectuer l'apprentissage, à l'aide du langage de requête DMX (Data Mining Extensions). Vous utiliserez ensuite ces modèles d'exploration pour établir des prédictions décrivant les produits susceptibles d'être achetés simultanément.  
  
 Les modèles d'exploration de données seront créés à partir des données de la société fictive [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] stockées dans l'exemple de base de données [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est une importante société de fabrication multinationale. L'entreprise fabrique et vend des vélos métalliques et des vélos en alliage sur les marchés nord-américain, européen et asiatique. Son siège qui compte 290 employés est situé à Bothell dans l'état de Washington aux États-Unis ; elle dispose de plusieurs équipes commerciales réparties dans diverses régions du monde constituant son marché de base.  
  
## <a name="tutorial-scenario"></a>Scénario du didacticiel  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] a choisi de créer une application personnalisée qui exploite des fonctionnalités d'exploration de données capables de prévoir les types de produits que ses clients sont susceptibles d'acheter en même temps. L'objectif de cette application personnalisée est de pouvoir spécifier un ensemble de produits et de prédire les autres produits qui seront achetés avec ces produits. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] utilisera ensuite ces informations pour ajouter un outil de « suggestion » sur son site Web et mieux organiser la manière dont l'information est présentée à ses clients.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fournit plusieurs outils qui peuvent être utilisés pour accomplir cette [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tâche :  
  
-   Langage de requête DMX  
  
-   [Algorithme Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)  
  
-   Éditeur de requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 Le langage de requête DMX (Data Mining Extensions) fourni par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] permet de créer et d'utiliser des modèles d'exploration de données. L' [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme d’association crée des modèles qui peuvent prédire les produits susceptibles d’être achetés ensemble.  
  
 L'objectif de ce didacticiel est de fournir des requêtes DMX à utiliser dans l'application personnalisée.  
  
 **Pour plus d’informations : solutions d'** [exploration de données](../../2014/analysis-services/data-mining/data-mining-solutions.md)  
  
## <a name="mining-structure-and-mining-models"></a>Structure et modèles d'exploration de données  
 Avant de créer des instructions DMX, il est primordial de comprendre les objets principaux auxquels [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fait appel pour créer des modèles d'exploration de données. La *structure d’exploration* de données est une structure de données qui définit le domaine de données à partir duquel les modèles d’exploration de données sont générés. Une structure d’exploration de données unique peut contenir plusieurs *modèles d’exploration de données* qui partagent le même domaine. Un modèle d'exploration applique un algorithme de modèle d'exploration aux données qui sont représentées par une structure d'exploration de données.  
  
 Les composants constituant la structure d'exploration de données sont les colonnes de structure d'exploration de données qui décrivent les données inscrites dans la source de données. Ces colonnes contiennent des informations, telles que le type de données, le type de contenu et le mode de distribution des données.  
  
 Les modèles d'exploration de données doivent contenir la colonne clé décrite dans la structure d'exploration de données, ainsi qu'un sous-ensemble des colonnes restantes. Le modèle d'exploration de données détermine l'usage de chaque colonne et définit l'algorithme utilisé pour sa création. Par exemple, dans DMX, vous pouvez définir une colonne comme étant une colonne clé ou une colonne PREDICT. Une colonne non définie est considérée comme une colonne d'entrée.  
  
 Deux méthodes permettent de créer des modèles d'exploration de données dans DMX. Vous pouvez soit créer ensemble la structure d'exploration de données et le modèle qui y est associé par le biais de l'instruction `CREATE MINING MODEL`, soit créer d'abord une structure d'exploration de données à l'aide de l'instruction `CREATE MINING STRUCTURE`, puis ajouter un modèle d'exploration de données à la structure à l'aide de l'instruction `ALTER STRUCTURE`. Ces méthodes sont décrites ci-dessous.  
  
 `CREATE MINING MODEL`  
 Utilisez cette instruction pour créer en même temps une structure d'exploration de données et son modèle associé en utilisant le même nom. Le nom du modèle d'exploration de données est ajouté à la mention « Structure » pour le différencier de la structure d'exploration de données.  
  
 Cette instruction est utile si vous créez une structure d'exploration de données conçue pour accueillir un seul modèle d'exploration de données.  
  
 Pour plus d’informations, consultez [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).  
  
 CREATE MINING STRUCTURE  
 Utilisez cette instruction pour créer une structure d'exploration de données sans modèle.  
  
 Lorsque vous utilisez CREATE MINING STRUCTURE, vous pouvez également créer un jeu de données d'exclusion qui peut être utilisé pour tester tous les modèles basés sur la même structure d'exploration de données.  
  
 Pour plus d’informations, consultez [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).  
  
 `ALTER MINING STRUCTURE`  
 Utilisez cette instruction pour ajouter un modèle d'exploration de données à une structure d'exploration de données existant déjà sur le serveur.  
  
 Plusieurs raisons peuvent vous inciter à ajouter plusieurs modèles d'exploration de données dans une structure d'exploration de données unique. Par exemple, vous pouvez créer plusieurs modèles d'exploration de données à l'aide de différents algorithmes pour savoir lequel fonctionne le mieux. Vous pouvez également créer plusieurs modèles d'exploration de données à l'aide du même algorithme, mais avec un paramètre défini différemment pour chaque modèle, afin de trouver la meilleure définition pour ce paramètre.  
  
 Pour plus d’informations, consultez [ALTER Mining STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).  
  
 Puisque vous allez créer une structure d'exploration de données dotée de plusieurs modèles d'exploration de données, vous devrez adopter la deuxième méthode de ce didacticiel.  
  
 **Pour plus d’informations**  
  
 [Informations de référence sur les extensions DMX (Data Mining Extensions &#40;dmx&#41;](/sql/dmx/data-mining-extensions-dmx-reference), [Présentation de l’instruction DMX Select](/sql/dmx/understanding-the-dmx-select-statement), de la [structure et de l’utilisation des requêtes de prédiction DMX](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel contient les leçons suivantes :  
  
 [Leçon 1 : Création de la structure d’exploration de données Market Basket](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `CREATE` pour créer des structures d'exploration de données.  
  
 [Leçon 2 : Ajout de modèles d’exploration de données à la structure d’exploration de données Market Basket](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `ALTER` pour ajouter des modèles d'exploration de données à une structure d'exploration de données.  
  
 [Leçon 3 : Traitement de la structure d'exploration de données Market Basket](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `INSERT INTO` pour traiter des structures d'exploration de données et les modèles qui y sont associés.  
  
 [Leçon 4 : Exécution de prédictions Market Basket](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `PREDICTION JOIN` pour établir des prédictions par rapport à des modèles d'exploration de données.  
  
## <a name="requirements"></a>Conditions requises  
 Avant d'entamer ce didacticiel, assurez-vous que les éléments suivants sont installés :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   Base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]  
  
 Pour des raisons de sécurité, les bases de données exemples ne sont pas installées par défaut. Pour installer les exemples de bases de données [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]officiels pour, [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) accédez à ou à la page d’hébergement Microsoft SQL Server exemples et projets de la Communauté dans la section Microsoft SQL Server des exemples de produits. Cliquez sur **Databases**, puis cliquez sur l'onglet **Releases** et sélectionnez les bases de données souhaitées.  
  
> [!NOTE]  
>  Lorsque vous parcourez les didacticiels, il est recommandé d'ajouter les boutons **Rubrique suivante** et **Rubrique précédente** dans la barre d'outils de l'afficheur de document.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel DMX pour les acheteurs de vélos](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [Didacticiel sur l’exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Leçon 3 : Génération d’un scénario de panier d’achat &#40;Didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
