---
title: "Le&#231;on&#160;1 : Cr&#233;er un projet de mod&#232;le tabulaire | Microsoft Docs"
ms.custom: ""
ms.date: "03/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 28
---
# Le&#231;on&#160;1 : Cr&#233;er un projet de mod&#232;le tabulaire
Dans cette leçon, vous allez créer un nouveau projet de modèle tabulaire vide dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Une fois que votre projet est créé, vous pouvez commencer à ajouter des données à l'aide de l'Assistant Importation de table. En plus de créer un nouveau projet, cette leçon inclut également une brève introduction à l'environnement de création de modèles tabulaires dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
Pour en savoir plus sur les différents types de projets de modèles tabulaires, consultez [Projets de modèles tabulaires &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md). Pour en savoir plus sur l’environnement de création de modèles tabulaires, consultez [Générateur de modèles tabulaires &#40;SSAS&#41;](../analysis-services/tabular-models/tabular-model-designer-ssas.md).  
  
Durée estimée pour effectuer cette leçon : **10 minutes**  
  
## Conditions préalables  
Cette rubrique constitue la première leçon du didacticiel de conception de modèle tabulaire. Pour effectuer cette leçon, vous devez avoir installé la base de données AdventureWorksDW sur une instance de SQL Server. Pour plus d’informations, consultez [Modélisation tabulaire &#40;didacticiel Adventure Works&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md).  
  
## Créer un projet de modèle tabulaire  
  
#### Pour créer un projet de modèle tabulaire  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]Fichier **de** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, sous **Installé**, cliquez sur **Business Intelligence**, sur **Analysis Services** et enfin sur **Projet tabulaire Analysis Services**.  
  
3.  Dans **Nom**, tapez **Modèle tabulaire AW Internet Sales**, puis spécifiez l’emplacement des fichiers du projet.  
  
    Par défaut, **Nom de solution** est le même que le nom du projet ; toutefois, vous pouvez taper un autre nom pour la solution.  
  
4.  Cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Concepteur de modèle tabulaire**, dans **Serveur d’espace de travail**, tapez le nom d’une instance de SQL Server 2016 Analysis Services où vous disposez d’autorisations d’administrateur de serveur, puis cliquez sur **Tester la connexion**.  
  
    L’instance de serveur d’espace de travail que vous spécifiez hébergera une base de données de modèle tabulaire avec le même nom que le projet pendant la création.   
      
6.  Dans **Niveau de compatibilité**, vérifiez que **SQL Server 2016 (1200)** est sélectionné, puis cliquez sur **OK**.   
      
    Si SQL Server 2016 (1200) n’apparaît pas dans la zone de liste Niveau de compatibilité, cela signifie que vous n’utilisez pas la dernière version de SQL Server Data Tools. Pour obtenir la version la plus récente, consultez [Installer les outils de données SQL Server](https://msdn.microsoft.com/hh500335(v=vs.103).aspx).   
      
    Sélectionner un niveau de compatibilité antérieur n’est recommandé que si vous envisagez de déployer votre modèle tabulaire terminé sur une autre instance d’Analysis Services exécutant SQL Server 2012 ou SQL Server 2014. Pour en savoir plus, consultez [Niveau de compatibilité](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).   
  
## Présentation de l'environnement de création du modèle tabulaire d'outils de données SQL Server  
Maintenant que vous avez créé un nouveau projet de modèle tabulaire, prenons un moment pour explorer l'environnement de création du modèle tabulaire dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 ou versions ultérieures).  
  
Une fois votre projet créé, il s'ouvre dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Un modèle vide apparaît dans le concepteur de modèles et le fichier **Model.bim** est sélectionné dans la fenêtre de **l’Explorateur de solutions**. Lorsque vous ajoutez des données, les tables et les colonnes apparaissent dans le concepteur. Si vous ne voyez pas le concepteur (la fenêtre vide avec l’onglet Model.bim), dans **l’Explorateur de solutions**, sous **Modèle tabulaire AW Internet Sales**, double-cliquez sur le fichier **Model.bim**.  
  
Vous pouvez afficher les propriétés du projet de base dans la fenêtre **Propriétés**. Dans **l’Explorateur de solutions**, cliquez sur **Modèle tabulaire AW Internet Sales**. Notez que dans la fenêtre **Propriétés**, dans **Fichier projet**, vous allez voir **Modèle tabulaire AW Internet Sales.smproj**. Il s’agit du nom du fichier du projet, avec son emplacement dans le champ **Dossier du projet**.  
  
Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet **Modèle tabulaire AW Internet Sales**, puis cliquez sur **Propriétés**. La boîte de dialogue **Pages des propriétés du modèle tabulaire AW Internet Sales** s’affiche. Ce sont les propriétés avancées du projet. Vous définirez ultérieurement certaines de ces propriétés lorsque vous serez prêt à déployer votre modèle.  
  
Maintenant, regardons les propriétés du modèle. Dans **l’Explorateur de solutions**, cliquez sur **Model.bim**. Dans la fenêtre **Propriétés**, vous pouvez voir maintenant les propriétés du modèle, dont la plus importante est la propriété **Mode DirectQuery**. Cette propriété indique si le modèle est déployé en mode In-Memory (désactivé) ou en mode DirectQuery (activé). Pour ce didacticiel, vous allez créer et déployer votre modèle en mode In-Memory.  
  
Lorsque vous créez un modèle, certaines de ses propriétés sont définies automatiquement selon les paramètres de modélisation des données qui peuvent être spécifiés dans la boîte de dialogue des outils et des options. Les propriétés de sauvegarde de données, de rétention de l'espace de travail et du serveur de l'espace de travail spécifient comment et où la base de données d'espace de travail (votre base de données de conception de modèle) est sauvegardée, conservée en mémoire et construite. Vous pouvez modifier ces paramètres ultérieurement si nécessaire, mais pour le moment, laissez ces propriétés telles qu'elles sont.  
  
Lorsque vous avez installé [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], plusieurs nouveaux éléments de menu ont été ajoutés à l'environnement Visual Studio. Regardons les éléments de menu spécifiques à la création de modèles tabulaires. Cliquez sur le menu **Modèle**. À partir de cette page, vous pouvez lancer l'Assistant Importation de table, afficher et modifier les connexions existantes, actualiser les données de l'espace de travail, parcourir votre modèle dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel avec la fonctionnalité d'analyse dans Excel, créer des perspectives et des rôles, sélectionner la vue du modèle et définir les options de calcul.  
  
Cliquez sur le menu **Table**. Ici, vous pouvez créer et gérer des relations entre des tables, créer, gérer et spécifier des paramètres de table Date, créer des partitions et modifier les propriétés de la table.  
  
Cliquez sur le menu **Colonne**. Ici, vous pouvez ajouter et supprimer des colonnes dans une table, figer des colonnes et spécifier l'ordre de tri. Vous pouvez également utiliser la fonction Somme automatique pour créer une mesure standard d'agrégation pour une colonne sélectionnée. D'autres boutons de la barre d'outils permettent d'accéder rapidement aux fonctionnalités et aux commandes fréquemment utilisées.  
  
Explorez les boîtes de dialogue et les emplacements des fonctionnalités spécifiques à la création des modèles tabulaires. Bien que certains éléments ne soient pas toujours actifs, vous pouvez avoir une bonne idée de l'environnement de création des modèles tabulaires.  
  
## Étapes suivantes  
Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 2 : Ajouter des données](../analysis-services/lesson-2-add-data.md).  
  
  
  
