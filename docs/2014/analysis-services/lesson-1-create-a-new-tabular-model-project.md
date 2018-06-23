---
title: 'Leçon 1 : Créer un nouveau projet de modèle tabulaire | Documents Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: 6a5f5c938289963373d09891f20c3a87495a33a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140403"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Leçon 1 : Créer un projet de modèle tabulaire
  Dans cette leçon, vous allez créer un nouveau projet de modèle tabulaire vide dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Une fois que votre projet est créé, vous pouvez commencer à ajouter des données à l'aide de l'Assistant Importation de table. En plus de créer un nouveau projet, cette leçon inclut également une brève introduction à l'environnement de création de modèles tabulaires dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 Pour en savoir plus sur les différents types de projets de modèles tabulaires, consultez [Projets de modèles tabulaires &#40;SSAS Tabulaire&#41;](tabular-models/tabular-model-projects-ssas-tabular.md). Pour en savoir plus sur l’environnement de création de modèle tabulaire, consultez [Concepteur de modèles tabulaires &#40;tabulaire SSAS&#41;](tabular-model-designer-ssas-tabular.md).  
  
 Durée estimée pour effectuer cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique constitue la première leçon du didacticiel de conception de modèle tabulaire. Pour effectuer cette leçon, vous devez avoir installé la base de données AdventureWorksDW sur une instance de SQL Server. Pour plus d’informations, consultez [Modélisation tabulaire &#40;didacticiel Adventure Works&#41;](tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Créer un projet de modèle tabulaire  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Pour créer un projet de modèle tabulaire  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]Fichier **de** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue **modèles installés**, cliquez sur **Business Intelligence**, puis cliquez sur **Analysis Services**, et puis cliquez sur **projet tabulaire Analysis Services**.  
  
3.  Dans **nom**, type `AW Internet Sales Tabular Model`, puis spécifiez l’emplacement des fichiers du projet.  
  
     Par défaut, **Nom de solution** est le même que le nom du projet ; toutefois, vous pouvez taper un autre nom pour la solution.  
  
4.  Cliquez sur **OK**.  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a>Présentation de l'environnement de création du modèle tabulaire d'outils de données SQL Server  
 Maintenant que vous avez créé un nouveau projet de modèle tabulaire, prenons un moment pour explorer l'environnement de création du modèle tabulaire dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 ou versions ultérieures).  
  
 Une fois votre projet créé, il s'ouvre dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Un modèle vide apparaît dans le concepteur de modèles et le fichier **Model.bim** est sélectionné dans la fenêtre de **l’Explorateur de solutions** . Lorsque vous ajoutez des données, les tables et les colonnes apparaissent dans le concepteur. Si vous ne voyez pas dans le concepteur (la fenêtre vide avec l’onglet Model.bim), **l’Explorateur de solutions**, sous `AW Internet Sales Tabular Model`, double-cliquez sur le **Model.bim** fichier.  
  
 Vous pouvez afficher les propriétés du projet de base dans la fenêtre **Propriétés** . Dans **l’Explorateur de solutions**, cliquez sur `AW Internet Sales Tabular Model`. Notez que dans la fenêtre **Propriétés** , dans **Fichier projet**, vous allez voir **Modèle tabulaire AW Internet Sales.smproj**. Il s’agit du nom du fichier du projet, avec son emplacement dans le champ **Dossier du projet**.  
  
 Dans **l’Explorateur de solutions**, cliquez sur le `AW Internet Sales Tabular Model` de projet, puis cliquez sur **propriétés**. La boîte de dialogue **Pages des propriétés du modèle tabulaire AW Internet Sales** s’affiche. Ce sont les propriétés avancées du projet. Vous définirez ultérieurement certaines de ces propriétés lorsque vous serez prêt à déployer votre modèle.  
  
 Maintenant, regardons les propriétés du modèle. Dans **l’Explorateur de solutions**, cliquez sur **Model.bim**. Dans la fenêtre **Propriétés** , vous pouvez voir maintenant les propriétés du modèle, dont la plus importante est la propriété **Mode DirectQuery** . Cette propriété indique si le modèle est déployé en mode In-Memory (désactivé) ou en mode DirectQuery (activé). Pour ce didacticiel, vous allez créer et déployer votre modèle en mode In-Memory.  
  
 Lorsque vous créez un modèle, certaines de ses propriétés sont définies automatiquement selon les paramètres de modélisation des données qui peuvent être spécifiés dans la boîte de dialogue des outils et des options. Les propriétés de sauvegarde de données, de rétention de l'espace de travail et du serveur de l'espace de travail spécifient comment et où la base de données d'espace de travail (votre base de données de conception de modèle) est sauvegardée, conservée en mémoire et construite. Vous pouvez modifier ces paramètres ultérieurement si nécessaire, mais pour le moment, laissez ces propriétés telles qu'elles sont.  
  
 Lorsque vous avez installé [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], plusieurs nouveaux éléments de menu ont été ajoutés à l'environnement Visual Studio. Regardons les éléments de menu spécifiques à la création de modèles tabulaires. Cliquez sur le menu **Modèle** . À partir de cette page, vous pouvez lancer l'Assistant Importation de table, afficher et modifier les connexions existantes, actualiser les données de l'espace de travail, parcourir votre modèle dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel avec la fonctionnalité d'analyse dans Excel, créer des perspectives et des rôles, sélectionner la vue du modèle et définir les options de calcul.  
  
 Cliquez sur le menu **Table**. Ici, vous pouvez créer et gérer des relations entre des tables, créer, gérer et spécifier des paramètres de table Date, créer des partitions et modifier les propriétés de la table.  
  
 Cliquez sur le menu **Colonne** . Ici, vous pouvez ajouter et supprimer des colonnes dans une table, figer des colonnes et spécifier l'ordre de tri. Vous pouvez également utiliser la fonction Somme automatique pour créer une mesure standard d'agrégation pour une colonne sélectionnée. D'autres boutons de la barre d'outils permettent d'accéder rapidement aux fonctionnalités et aux commandes fréquemment utilisées.  
  
 Explorez les boîtes de dialogue et les emplacements des fonctionnalités spécifiques à la création des modèles tabulaires. Bien que certains éléments ne soient pas toujours actifs, vous pouvez avoir une bonne idée de l'environnement de création des modèles tabulaires.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 2 : Ajouter des données](lesson-2-add-data.md).  
  
  