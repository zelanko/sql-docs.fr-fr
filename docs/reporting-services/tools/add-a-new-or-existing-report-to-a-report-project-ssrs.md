---
title: "Ajouter un nouveau rapport ou un rapport existant &#224; un projet de rapport (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rapports [Reporting Services], création"
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Ajouter un nouveau rapport ou un rapport existant &#224; un projet de rapport (SSRS)
  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez ajouter un nouveau rapport paginé [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] en utilisant l’Assistant Rapport ou en ajoutant un nouveau rapport vide à votre projet. Vous pouvez aussi ajouter un rapport existant. Après avoir ajouté un rapport, vous pouvez voir son nom sous le dossier **Rapports** de votre projet.  
  
> [!NOTE]  
>  Pour afficher l'aperçu d'un rapport avec les sources de données existantes, vous devez disposer d'autorisations sur la source de données à partir du client de création de votre rapport. Pour plus d’informations, consultez [Connexions de données, sources de données et chaînes de connexion](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
 Après avoir ajouté un rapport, vous pouvez définir des sources de données et des datasets, ainsi que concevoir la mise en page du rapport. Pour commencer, consultez [Créer un rapport de table de base &#40;didacticiel SSRS&#41;](../../reporting-services/create-a-basic-table-report-ssrs-tutorial.md) ou [Tables &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md).  
  
## Pour ajouter un nouveau rapport en utilisant l'Assistant Rapport  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier Rapports, puis sélectionnez **Ajouter un nouveau rapport**. La boîte de dialogue **Assistant Rapport** s’ouvre.  
  
     Les étapes de l'Assistant vous guident à travers la création d'une source de données, la création d'un dataset avec une requête, la définition de groupes, la spécification d'une mise en page, le choix d'un style qui inclut la couleur et la police, et la création du rapport. Les étapes sont les suivantes :  
  
    -   **Sélectionnez une source de données.** La première étape de création d'un rapport consiste à définir une source de données. L'Assistant Rapport fournit la liste de toutes les sources de données partagées du projet de rapport et offre la possibilité de créer une nouvelle source de données.  
  
    -   **Créez une requête.** L'étape suivante consiste à créer une requête. Vous pouvez taper la chaîne de requête, la générer à l'aide du concepteur de requêtes ou importer une requête à partir d'un autre rapport. Pour plus d’informations sur les concepteurs de requêtes, consultez [Concepteurs de requêtes Reporting Services](../Topic/Reporting%20Services%20Query%20Designers.md).  
  
    -   **Choisissez un type de rapport.** L'étape suivante consiste à sélectionner le type de rapport souhaité. Vous pouvez choisir un rapport tabulaire ou de matrice. Un rapport tabulaire comporte un nombre fixe de colonnes. Un rapport de matrice (ou tableau croisé dynamique) comporte un nombre variable de colonnes qui dépend des résultats de la requête. Un rapport cartographique affiche des informations analytiques sur un arrière-plan géographique.  
  
    -   **Choisissez un style.** L'étape suivante consiste à appliquer un style au rapport en utilisant un modèle de style. Sélectionnez un modèle pour appliquer au rapport des styles comme des polices, des couleurs et des styles de bordure. Le Concepteur de rapports fournit six modèles de style : Ardoise, Forêt, Entreprise, Gras, Océan et Générique. Vous pouvez également ajouter des modèles de style supplémentaires.  
  
        > [!NOTE]  
        >  Vous pouvez modifier des modèles existants ou en ajouter de nouveaux en modifiant le fichier StyleTemplates.xml du dossier \Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<langue\>, où \<langue> désigne la langue que vous utilisez (par exemple, si vous utilisez la version française de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], le nom du dossier est « FR »). Ce dossier se trouve sur l'ordinateur sur lequel le Concepteur de rapports est installé. Il existe deux exemplaires du fichier StyleTemplates.xml. Pour modifier les styles appliqués via l'Assistant Rapport, modifiez le fichier qui est dans le dossier créé pour la langue que vous utilisez.  
  
    -   **Nommez le rapport.**  La dernière étape consiste à donner un nom au rapport et à vérifier les champs qui y seront inclus. Lorsque la procédure est terminée, le Concepteur de rapports crée le rapport et l'ajoute au projet du serveur de rapports.  
  
## Pour ajouter un rapport vide  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans **Modèles**, cliquez sur **Rapport**.  
  
3.  Cliquez sur **Ajouter**.  
  
     Un nouveau rapport vide est ajouté au projet et affiché sur l'aire de conception.  
  
## Pour ajouter un rapport existant  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter**, puis sur **Élément existant**.  
  
2.  Naviguez jusqu’à l’emplacement du fichier .rdl, sélectionnez-le, puis cliquez sur **Ajouter**.  
  
     Le rapport est ajouté au projet sous le dossier **Rapports**. Lorsque vous fermez et rouvrez le projet, les rapports sont triés alphabétiquement.  
  
## Voir aussi  
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](../../reporting-services/reporting-services-tutorials-ssrs.md)  
  
  