---
title: "Le&#231;on&#160;13&#160;: Analyser dans Excel | Microsoft Docs"
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
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
caps.latest.revision: 22
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on&#160;13&#160;: Analyser dans Excel
Dans cette leçon, vous allez utiliser la fonction Analyser dans Excel dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour ouvrir Microsoft Excel, créer automatiquement une connexion de source de données à l'espace de travail du modèle et ajouter automatiquement un tableau croisé dynamique à la feuille de calcul. La fonction Analyser dans Excel offre un moyen simple et rapide de tester l'efficacité de votre conception de modèle avant de le déployer. Vous n'allez exécuter aucune analyse de données dans cette leçon. L'objectif de cette leçon est de vous familiariser, en tant qu'auteur de modèle, avec les outils que vous pouvez utiliser pour tester votre conception de modèle. Contrairement à la fonctionnalité Analyser dans Excel, qui est destinée aux auteurs de modèle, les utilisateurs finaux utilisent les applications de création de rapports clientes, par exemple Excel ou [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], pour se connecter aux données du modèle déployé et les parcourir.  
  
Pour pouvoir exécuter cette leçon, Excel doit être installé sur le même ordinateur que [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Pour en savoir plus, consultez [Analyser dans Excel &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md).  
  
Durée estimée pour effectuer cette leçon : **20 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 11 : Créer des partitions](../analysis-services/lesson-11-create-partitions.md).  
  
## Parcourir des données à l'aide des perspectives par défaut et Internet Sales  
Dans ces premières tâches, vous pourrez parcourir votre modèle à l'aide de la perspective par défaut, qui inclut tous les objets de modèle, et de la perspective Internet Sales que vous avez créée dans la leçon 8 : créer des perspectives. La perspective Internet Sales exclut l'objet table Customer.  
  
#### Pour parcourir les données à l'aide de la perspective par défaut  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle**, puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel**, cliquez sur **OK**.  
  
    Excel s'ouvre avec un nouveau classeur. Une connexion de source de données est créée à l'aide du compte d'utilisateur actuel et la perspective par défaut est utilisée pour définir les champs visibles. Un tableau croisé dynamique est automatiquement ajouté à la feuille de calcul.  
  
3.  Dans Excel, dans la **Liste de champs de tableau croisé dynamique**, notez que les groupes de mesures **Date** et **Internet Sales** s’affichent, ainsi que les tables **Customer**, **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory **et **Internet Sales** avec leurs colonnes respectives.  
  
4.  Fermez Excel sans enregistrer le classeur.  
  
#### Pour parcourir les données à l'aide de perspective Internet Sales  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle**, puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel**, laissez **Utilisateur Windows actuel** sélectionné, puis dans la zone de liste déroulante **Perspective**, sélectionnez **Internet Sales**, puis cliquez sur **OK**. Excel s'ouvre.  
  
3.  Dans Excel, dans la **Liste de champs de tableau croisé dynamique**, notez que la table Customer est exclue de la liste de champs.  
  
4.  Fermez Excel sans enregistrer le classeur.  
  
## Parcourir les données à l'aide de rôles  
Les rôles font partie intégrante de n’importe quel modèle tabulaire. Sans disposer d'au moins un rôle auquel les utilisateurs sont ajoutés en tant que membres, ces derniers ne peuvent pas accéder aux données et les analyser à l'aide de votre modèle. La fonctionnalité Analyser dans Excel vous fournit un moyen de tester les rôles que vous avez définis.  
  
#### Pour parcourir les données à l'aide du rôle utilisateur Sales Manager  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle**, puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel**, dans **Spécifier le nom d’utilisateur ou le rôle à utiliser pour se connecter au modèle**, sélectionnez **Rôle**, puis dans la zone de liste déroulante, sélectionnez **Internet Sales Manager**, puis cliquez sur **OK**.  
  
    Excel s'ouvre avec un nouveau classeur. Un tableau croisé dynamique est créé automatiquement. La liste des champs du tableau croisé dynamique inclut tous les champs de données disponibles dans votre nouveau modèle.  
      
3.  Fermez Excel sans enregistrer le classeur.  
  
## Étapes suivantes  
Pour continuer ce didacticiel, passez à la [Leçon 14 : Déployer](../analysis-services/lesson-14-deploy.md).  
  
  
  
