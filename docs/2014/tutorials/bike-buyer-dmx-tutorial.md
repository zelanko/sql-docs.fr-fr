---
title: Bike Buyer DMX Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 4b634cc1-86dc-42ec-9804-a19292fe8448
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3cf9a0c9e6059330c0b8edbd8228f617ba093564
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56025250"
---
# <a name="bike-buyer-dmx-tutorial"></a>Didacticiel DMX Bike Buyer
  Dans ce didacticiel, vous allez apprendre à créer, assimiler et explorer des modèles d'exploration de données à l'aide du langage de requête DMX (Data Mining Extensions). Vous utiliserez ensuite ces modèles pour créer des tâches de prédiction déterminant si un client envisage ou non d'acheter un vélo.  
  
 Les modèles d'exploration de données seront créés à partir des données de la société fictive [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] stockées dans l'exemple de base de données [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]. [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] est une importante société de fabrication multinationale. L'entreprise fabrique et vend des vélos métalliques et des vélos en alliage sur les marchés nord-américain, européen et asiatique. Son siège qui compte 290 employés est situé à Bothell dans l'état de Washington aux États-Unis ; elle dispose de plusieurs équipes commerciales réparties dans diverses régions du monde constituant son marché de base.  
  
## <a name="tutorial-scenario"></a>Scénario du didacticiel  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] a décidé d'étendre l'analyse de ses données en créant une application personnalisée qui exploite des fonctionnalités d'exploration de données. Son application personnalisée vise les objectifs suivants :  
  
-   Recueillir en guise de données les caractéristiques spécifiques d'un client potentiel et déterminer son intention ou non d'acheter un vélo.  
  
-   Recueillir en guise de données une liste de clients potentiels et les caractéristiques de ces clients, puis déterminer les clients susceptibles d'acheter des vélos.  
  
 Dans le premier cas, les données des clients proviennent d'une page d'enregistrement des clients ; dans le deuxième cas, une liste de clients potentiels est obtenue auprès du service marketing de [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] .  
  
 Qui plus est, le service marketing demande s'il est possible de regrouper des clients existants par catégories selon diverses caractéristiques, notamment le lieu de résidence, le nombre d'enfants à charge et la distance parcourue pour se rendre au travail et en revenir. Les responsables de ce service souhaitent savoir s'il est possible d'utiliser ces clusters pour cibler des catégories précises de clients. Cette recherche exige un autre modèle d'exploration de données.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fournit plusieurs outils qui peuvent être utilisées pour accomplir ces tâches :  
  
-   Langage de requête DMX  
  
-   Algorithmes [Microsoft Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) et [Microsoft Clustering](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)  
  
-   Éditeur de requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
 Le langage de requête DMX (Data Mining Extensions) fourni par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] permet de créer et d'utiliser des modèles d'exploration de données. L'algorithme MDT ( [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees) permet de créer des modèles que vous pouvez utiliser pour prévoir les intentions d'achat de vélo d'une personne. Le modèle obtenu permet d'exploiter un seul client ou un ensemble de clients en guise de données. L'algorithme [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering permet de créer des groupes de clients sur la base de caractéristiques communes. L'objectif de ce didacticiel est de fournir des scripts DMX à utiliser dans l'application personnalisée.  
  
 **Pour plus d'informations, consultez :** [Solutions d'exploration de données](../../2014/analysis-services/data-mining/data-mining-solutions.md)  
  
## <a name="mining-structure-and-mining-models"></a>Structure et modèles d'exploration de données  
 Avant de créer des instructions DMX, il est primordial de comprendre les objets principaux auxquels [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] fait appel pour créer des modèles d'exploration de données. La structure d'exploration de données est une structure de données qui définit le domaine de données à partir duquel les modèles d'exploration de données sont créés. Une structure d'exploration de données unique peut contenir plusieurs de ces modèles partageant le même domaine. Un modèle d'exploration applique un algorithme de modèle d'exploration aux données qui sont représentées par une structure d'exploration de données.  
  
 Les composants constituant la structure d'exploration de données sont les colonnes de structure d'exploration de données qui décrivent les données inscrites dans la source de données. Ces colonnes contiennent des informations, telles que le type de données, le type de contenu et le mode de distribution des données.  
  
 Les modèles d'exploration de données doivent contenir la colonne clé décrite dans la structure d'exploration de données, ainsi qu'un sous-ensemble des colonnes restantes. Le modèle d'exploration de données détermine l'usage de chaque colonne et définit l'algorithme utilisé pour sa création. Par exemple, dans DMX, vous pouvez définir une colonne comme étant une colonne clé ou une colonne PREDICT. Une colonne non définie est considérée comme une colonne d'entrée.  
  
 Deux méthodes permettent de créer des modèles d'exploration de données dans DMX. Vous pouvez soit créer ensemble la structure d'exploration de données et le modèle qui y est associé par le biais de l'instruction CREATE MINING MODEL, soit créer d'abord une structure d'exploration de données à l'aide de l'instruction CREATE MINING STRUCTURE, puis ajouter un modèle d'exploration de données à la structure à l'aide de l'instruction ALTER STRUCTURE. Ces méthodes sont décrites dans le tableau ci-dessous.  
  
 CREATE MINING MODEL  
 Utilisez cette instruction pour créer en même temps une structure d'exploration de données et son modèle associé en utilisant le même nom. Le nom du modèle d'exploration de données est ajouté à la mention « Structure » pour le différencier de la structure d'exploration de données. Cette instruction est utile si vous créez une structure d'exploration de données conçue pour accueillir un seul modèle d'exploration de données.  
  
 Pour plus d’informations, consultez [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).  
  
 ALTER MINING STRUCTURE  
 Utilisez cette instruction pour ajouter un modèle d'exploration de données à une structure d'exploration de données existant déjà sur le serveur. Cette instruction est utile si vous souhaitez créer une structure d'exploration de données abritant plusieurs modèles d'exploration de données différents. Plusieurs raisons peuvent vous inciter à ajouter plusieurs modèles d'exploration de données dans une structure d'exploration de données unique. Par exemple, vous pouvez créer plusieurs modèles d'exploration de données utilisant différents algorithmes pour savoir lequel fonctionne le mieux. Vous pouvez créer plusieurs modèles d'exploration de données utilisant le même algorithme, mais avec un paramètre défini différemment pour chaque modèle, afin de trouver la meilleure définition pour ce paramètre.  
  
 Pour plus d’informations, consultez [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).  
  
 Puisque vous allez créer une structure d'exploration de données dotée de plusieurs modèles d'exploration de données, vous devrez adopter la deuxième méthode de ce didacticiel.  
  
 **Pour plus d’informations**  
  
 [Data Mining Extensions &#40;DMX&#41; référence](/sql/dmx/data-mining-extensions-dmx-reference), [présentation de l’instruction DMX instruction Select](/sql/dmx/understanding-the-dmx-select-statement), [Structure et utilisation des requêtes de prédiction DMX](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel contient les leçons suivantes :  
  
 [Leçon 1 : Création de la Structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `CREATE` pour créer des structures d'exploration de données.  
  
 [Leçon 2 : Ajout des modèles d’exploration de données à la Structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `ALTER` pour ajouter des modèles d'exploration de données à une structure d'exploration de données.  
  
 [Leçon 3 : Traitement de la Structure d’exploration de données Bike Buyer](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `INSERT INTO` pour traiter des structures d'exploration de données et les modèles qui y sont associés.  
  
 [Leçon 4 : Exploration des modèles d’exploration de données Bike Buyer](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `SELECT` pour explorer le contenu des modèles d'exploration de données.  
  
 [Leçon 5 : L’exécution de requêtes de prédiction](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
 Dans cette leçon, vous allez apprendre à utiliser l'instruction `PREDICTION JOIN` pour établir des prédictions par rapport à des modèles d'exploration de données.  
  
## <a name="requirements"></a>Configuration requise  
 Avant d'entamer ce didacticiel, assurez-vous que les éléments suivants sont installés :  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)], [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], ou [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   La base de données [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] . Pour des raisons de sécurité, les bases de données exemples ne sont pas installées par défaut. Pour installer des exemples de bases de données officielles pour [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visitez la page d' [exemples de bases de données Microsoft SQL](https://go.microsoft.com/fwlink/?LinkId=88417) (en anglais) et sélectionnez les bases de données que vous voulez installer.  
  
> [!NOTE]  
>  Lorsque vous parcourez les didacticiels, il est recommandé d'ajouter les boutons **Rubrique suivante** et **Rubrique précédente** dans la barre d'outils de l'afficheur de document.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel DMX Market Basket](../../2014/tutorials/market-basket-dmx-tutorial.md)   
 [Tutoriel sur l’exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
  
