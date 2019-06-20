---
title: 'Leçon 1 : Créez un projet de modèle tabulaire | Microsoft Docs'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 293b4aa3e1723fa5376e3658e65e4da2104acad4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404811"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Leçon 1 : Créer un projet de modèle tabulaire
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

Dans cette leçon, vous allez créer un nouveau projet de modèle tabulaire vide dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Une fois que votre projet est créé, vous pouvez commencer à ajouter des données à l'aide de l'Assistant Importation de table. Cette leçon vous présente également une brève introduction à l’environnement dans SSDT de création de modèle tabulaire.  
  
Durée estimée pour effectuer cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
Cette rubrique constitue la première leçon du didacticiel de conception de modèle tabulaire. Pour suivre cette leçon, vous devez disposer de la base de données exemple AdventureWorksDW installée sur une instance de SQL Server. Pour plus d’informations, consultez [modélisation tabulaire &#40;didacticiel Adventure Works&#41;](tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Créer un projet de modèle tabulaire  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Pour créer un projet de modèle tabulaire  
  
1.  Dans SSDT, sur le **fichier** menu, cliquez sur **New** > **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez **installé** > **Business Intelligence** > **Analysis Services**, puis cliquez sur **projet tabulaire Analysis Services**.  
  
3.  Dans **nom**, type **AW Internet Sales**, puis spécifiez un emplacement pour les fichiers de projet.  
  
    Par défaut, **Nom de solution** est le même que le nom du projet ; toutefois, vous pouvez taper un autre nom pour la solution.  
  
4.  Cliquez sur **OK**.  
  
5.  Dans le **Générateur de modèles tabulaires** boîte de dialogue, sélectionnez **espace de travail intégré**.  
  
    L’espace de travail hébergera une base de données de modèle tabulaire portant le même nom que le projet pendant la création du modèle. Espace de travail intégré signifie que SSDT utilisera une instance intégrée, en éliminant le besoin d’installer une instance de serveur Analysis Services distincte uniquement pour la création du modèle. Pour plus d’informations, consultez [base de données de l’espace de travail](../tabular-models/workspace-database-ssas-tabular.md).
      
6.  Dans **Niveau de compatibilité**, vérifiez que **SQL Server 2016 (1200)** est sélectionné, puis cliquez sur **OK**.   
 
    ![as-tabular-lesson1-tmd](media/as-tabular-lesson1-tmd.png)
      
    Si vous ne voyez pas SQL Server 2016 RTM (1200) dans la zone de liste de niveau de compatibilité, vous n’utilisez pas la dernière version de SQL Server Data Tools. Pour obtenir la version la plus récente, consultez [Installer les outils de données SQL Server](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt).  

    Si vous utilisez la dernière version de SSDT, vous pouvez également choisir SQL Server 2017 (1400). Toutefois, pour la leçon 13 : Déployer, vous aurez besoin d’un SQL Server 2017 ou le serveur Azure pour déployer sur.
      
    En sélectionnant un niveau de compatibilité est recommandée uniquement si vous envisagez de déployer votre modèle tabulaire terminé vers une autre instance d’Analysis Services exécutant une version antérieure de SQL Server. Espace de travail intégré n’est pas pris en charge pour les niveaux de compatibilité antérieurs. Pour en savoir plus, consultez [Niveau de compatibilité](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).   
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>Présentation du modèle tabulaire SSDT environnement de création  
Maintenant que vous avez créé un nouveau projet de modèle tabulaire, prenons un moment pour Explorer le modèle tabulaire, environnement de création dans SSDT.  
  
Une fois votre projet est créé, il s’ouvre dans SSDT. Sur le côté droit, dans **Explorateur de modèles tabulaires**, vous verrez une arborescence des objets dans votre modèle. Étant donné que vous n’avez pas encore importé de données, les dossiers sera vides. Vous pouvez cliquer sur un dossier de l’objet pour effectuer des actions, similaires à la barre de menus. À mesure que vous parcourez ce didacticiel, vous allez utiliser l’Explorateur de modèles tabulaires pour naviguer parmi les différents objets dans votre projet de modèle.

![as-tabular-lesson1-tme](media/as-tabular-lesson1-tme.png)

Cliquez sur le **l’Explorateur de solutions** onglet. Ici, vous verrez votre **Model.bim** fichier. Si vous ne voyez pas la fenêtre du concepteur vers la gauche (la fenêtre vide avec l’onglet Model.bim), dans **l’Explorateur de solutions**, sous **projet AW Internet Sales**, double-cliquez sur le **Model.bim** fichier. Le fichier Model.bim contient toutes les métadonnées pour votre projet de modèle. 

![as-tabular-lesson1-se](media/as-tabular-lesson1-se.png)
  
Examinons les propriétés du modèle. Cliquez sur **Model.bim**. Dans le **propriétés** fenêtre, vous verrez la [des propriétés de modèle](../tabular-models/model-properties-ssas-tabular.md), la plus importante qui est la **DirectQuery Mode** propriété. Cette propriété indique si le modèle est déployé en mode In-Memory (désactivé) ou en mode DirectQuery (activé). Pour ce didacticiel, vous allez créer et déployer votre modèle en mode In-Memory.

![en tant que-tabulaire-lesson1-properties](media/as-tabular-lesson1-properties.png)
  
Lorsque vous créez un nouveau modèle, certaines de ses propriétés sont définies automatiquement en fonction des paramètres de modélisation des données qui peuvent être spécifiés dans le **outils** > **Options** boîte de dialogue. Les propriétés de sauvegarde de données, de rétention de l'espace de travail et du serveur de l'espace de travail spécifient comment et où la base de données d'espace de travail (votre base de données de conception de modèle) est sauvegardée, conservée en mémoire et construite. Vous pouvez modifier ces paramètres ultérieurement si nécessaire, mais pour le moment, laissez ces propriétés telles qu'elles sont.  

Dans **l’Explorateur de solutions**, avec le bouton droit **AW Internet Sales** (projet), puis cliquez sur **propriétés**. Le **Pages de propriétés de AW Internet Sales** boîte de dialogue s’affiche. Il s’agit des avancées [propriétés de projet](../tabular-models/project-properties-ssas-tabular.md). Vous définirez ultérieurement certaines de ces propriétés lorsque vous serez prêt à déployer votre modèle.  
  
Lorsque vous avez installé SSDT, plusieurs nouveaux éléments de menu ont été ajoutées à l’environnement Visual Studio. Examinons ceux spécifiques à la création de modèles tabulaires. Cliquez sur le menu **Modèle** . À ce stade, vous pouvez lancer l’Assistant Importation de Table afficher et modifier les connexions existantes, actualiser les données de l’espace de travail, parcourir votre modèle dans Excel avec la fonctionnalité analyser dans Excel, créer des perspectives et des rôles, sélectionner la vue du modèle et définir les options de calcul.  
  
Cliquez sur le menu **Table** . Ici, vous pouvez créer et gérer des relations entre des tables, créer, gérer et spécifier des paramètres de table Date, créer des partitions et modifier les propriétés de la table.  
  
Cliquez sur le menu **Colonne** . Ici, vous pouvez ajouter et supprimer des colonnes dans une table, figer des colonnes et spécifier l'ordre de tri. Vous pouvez également utiliser la fonction Somme automatique pour créer une mesure standard d'agrégation pour une colonne sélectionnée. D'autres boutons de la barre d'outils permettent d'accéder rapidement aux fonctionnalités et aux commandes fréquemment utilisées.  
  
Explorez les boîtes de dialogue et les emplacements des fonctionnalités spécifiques à la création des modèles tabulaires. Bien que certains éléments ne soient pas toujours actifs, vous pouvez avoir une bonne idée de l'environnement de création des modèles tabulaires.  


## <a name="additional-resources"></a>Ressources supplémentaires
Pour en savoir plus sur les différents types de projets de modèles tabulaires, consultez [projets de modèles tabulaires](../tabular-models/tabular-model-projects-ssas-tabular.md). Pour en savoir plus sur l’environnement de création de modèles tabulaires, consultez [Générateur de modèles tabulaires](../tabular-models/tabular-model-designer-ssas.md).  
  

## <a name="whats-next"></a>Quelle est l’étape suivante ?
Accédez à la leçon suivante : [Leçon 2 : Ajouter des données](lesson-2-add-data.md).

  
  
  
