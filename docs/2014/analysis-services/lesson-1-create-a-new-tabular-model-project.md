---
title: 'Leçon 1 : créer un projet de modèle tabulaire | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: f21d1805eda75bfa0008214e2f46f54b67ab48f5
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543596"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Leçon 1 : Créer un projet de modèle tabulaire
  Dans cette leçon, vous allez créer un nouveau projet de modèle tabulaire vide dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Une fois que votre projet est créé, vous pouvez commencer à ajouter des données à l'aide de l'Assistant Importation de table. En plus de créer un nouveau projet, cette leçon inclut également une brève introduction à l'environnement de création de modèles tabulaires dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 Pour en savoir plus sur les différents types de projets de modèles tabulaires, consultez [Projets de modèles tabulaires &#40;SSAS Tabulaire&#41;](tabular-models/tabular-model-projects-ssas-tabular.md). Pour en savoir plus sur l’environnement de création de modèles tabulaires, consultez [Concepteur de modèles tabulaires &#40;&#41;SSAS tabulaire ](tabular-model-designer-ssas-tabular.md).  
  
 Durée estimée pour suivre cette leçon : **10 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique constitue la première leçon du didacticiel de conception de modèle tabulaire. Pour effectuer cette leçon, vous devez avoir installé la base de données AdventureWorksDW sur une instance de SQL Server. Pour plus d’informations, consultez [Modélisation tabulaire &#40;didacticiel Adventure Works&#41;](tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Créer un projet de modèle tabulaire  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Pour créer un projet de modèle tabulaire  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]Fichier **de** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **nouveau projet** , sous **modèles installés**, cliquez sur **Business Intelligence**, sur **Analysis Services**, puis sur **Analysis Services projet tabulaire**.  
  
3.  Dans **nom**, tapez `AW Internet Sales Tabular Model` , puis spécifiez un emplacement pour les fichiers projet.  
  
     Par défaut, le **Nom de la solution** est identique au nom du projet ; toutefois, vous pouvez taper un nom de solution différent.  
  
4.  Cliquez sur **OK**.  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a>Présentation de l'environnement de création du modèle tabulaire d'outils de données SQL Server  
 Maintenant que vous avez créé un nouveau projet de modèle tabulaire, prenons un moment pour explorer l’environnement de création de modèle tabulaire dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 ou version ultérieure).  
  
 Une fois votre projet créé, il s'ouvre dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Un modèle vide apparaît dans le concepteur de modèles et le fichier **Model.bim** est sélectionné dans la fenêtre de **l’Explorateur de solutions** . Lorsque vous ajoutez des données, les tables et les colonnes apparaissent dans le concepteur. Si vous ne voyez pas le concepteur (la fenêtre vide avec l’onglet Model. BIM), dans **Explorateur de solutions**, sous `AW Internet Sales Tabular Model` , double-cliquez sur le fichier **Model. BIM** .  
  
 Vous pouvez afficher les propriétés du projet de base dans la fenêtre **Propriétés** . Dans **Explorateur de solutions**, cliquez sur `AW Internet Sales Tabular Model` . Notez que dans la fenêtre **Propriétés** , dans **Fichier projet**, vous allez voir **Modèle tabulaire AW Internet Sales.smproj**. Il s’agit du nom du fichier du projet, avec son emplacement dans le champ **Dossier du projet**.  
  
 Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `AW Internet Sales Tabular Model` projet, puis cliquez sur **Propriétés**. La boîte de dialogue **Pages des propriétés du modèle tabulaire AW Internet Sales** s’affiche. Il s’agit des propriétés de projet avancées. Vous définirez ultérieurement certaines de ces propriétés lorsque vous serez prêt à déployer votre modèle.  
  
 À présent, examinons les propriétés du modèle. Dans **l’Explorateur de solutions**, cliquez sur **Model.bim**. Dans la fenêtre **Propriétés** , vous pouvez voir maintenant les propriétés du modèle, dont la plus importante est la propriété **Mode DirectQuery** . Cette propriété spécifie si le modèle est déployé, ou non, en mode In-Memory (Désactivé) ou en mode DirectQuery (Activé). Pour ce didacticiel, vous allez créer et déployer votre modèle en mode In-Memory.  
  
 Lorsque vous créez un modèle, certaines de ses propriétés sont définies automatiquement selon les paramètres de modélisation des données qui peuvent être spécifiés dans la boîte de dialogue des outils et des options. Les propriétés de sauvegarde de données, de rétention de l'espace de travail et du serveur de l'espace de travail spécifient comment et où la base de données d'espace de travail (votre base de données de conception de modèle) est sauvegardée, conservée en mémoire et construite. Vous pouvez modifier ces paramètres ultérieurement si nécessaire, mais pour l’instant, laissez ces propriétés en l’état.  
  
 Lorsque vous avez installé [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], plusieurs nouveaux éléments de menu ont été ajoutés à l'environnement Visual Studio. Examinons les nouveaux éléments de menu spécifiques à la création de modèles tabulaires. Cliquez sur le menu **Modèle**. À partir de cette page, vous pouvez lancer l'Assistant Importation de table, afficher et modifier les connexions existantes, actualiser les données de l'espace de travail, parcourir votre modèle dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel avec la fonctionnalité d'analyse dans Excel, créer des perspectives et des rôles, sélectionner la vue du modèle et définir les options de calcul.  
  
 Cliquez sur le menu **Table** . Ici, vous pouvez créer et gérer des relations entre des tables, créer, gérer et spécifier des paramètres de table Date, créer des partitions et modifier les propriétés de la table.  
  
 Cliquez sur le menu **Colonne** . Ici, vous pouvez ajouter et supprimer des colonnes dans une table, figer des colonnes et spécifier l'ordre de tri. Vous pouvez également utiliser la fonction Somme automatique pour créer une mesure standard d'agrégation pour une colonne sélectionnée. D'autres boutons de la barre d'outils permettent d'accéder rapidement aux fonctionnalités et aux commandes fréquemment utilisées.  
  
 Explorez les boîtes de dialogue et les emplacements des fonctionnalités spécifiques à la création des modèles tabulaires. Bien que certains éléments ne soient pas toujours actifs, vous pouvez avoir une bonne idée de l'environnement de création des modèles tabulaires.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 2 : Ajouter des données](lesson-2-add-data.md).  
  
  
