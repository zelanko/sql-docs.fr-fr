---
title: 'Leçon 1 : Créer un projet Report Server | Microsoft Docs'
description: Dans cette leçon, vous créez un projet Report Server et un fichier de définition de rapport (.rdl) dans le Concepteur de rapports.
ms.date: 12/09/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ac84fb8cf355103b28fbac8f5411943aa4ee51a8
ms.sourcegitcommit: 22e97435c8b692f7612c4a6d3fe9e9baeaecbb94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92679049"
---
# <a name="lesson-1-create-a-report-server-project-reporting-services"></a>Leçon 1 : créer un projet Report Server (Reporting Services)

Dans cette leçon, vous créez un *projet Report Server* et un fichier de *définition de rapport (.rdl)* dans le *Concepteur de rapports* .

> [!NOTE]
> [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] est un environnement [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour créer des solutions d’aide à la décision. SSDT comprend l’environnement de création Concepteur de rapports, où vous pouvez ouvrir, modifier, afficher un aperçu, enregistrer et déployer des définitions de rapport paginés [!INCLUDE[ssrsnoversion_md](../includes/ssrsnoversion-md.md)] , des sources de données partagées, des datasets partagés et des parties de rapports.

Quand vous créez des rapports avec le Concepteur de rapports, il crée un projet Report Server qui contient les fichiers de rapports et autres fichiers de ressources utilisés par les rapports.

## <a name="to-create-a-report-server-project"></a>Pour créer un projet Report Server
  
1. Dans le menu **Fichier** , sélectionnez **Nouveau** > **Projet** .  

    ![Capture d’écran de Visual Studio montrant l’option Fichier > Nouveau > Projet sélectionnée.](../reporting-services/media/ssrs-ssdt-file-01-new-project.png)
  
2. Dans la colonne la plus à gauche sous **Installé** , sélectionnez **Reporting Services** . Dans certains cas, cette option peut se trouver sous le groupe **Business Intelligence** .

    ![Capture d’écran de la boîte de dialogue Nouveau projet montrant Reporting Services sélectionné et le modèle Projet Report Server mis en évidence.](../reporting-services/media/lesson-1-creating-a-report-server-project-reporting-services/select-report-server-project-template.png)

    > [!IMPORTANT]
    > Pour Visual Studio, si vous ne voyez pas Reporting Services dans la colonne de gauche, ajoutez le Concepteur de rapports en installant la charge de travail SSDT. Dans le menu **Outils** , sélectionnez **Obtenir les outils et fonctionnalités** et sélectionnez **SQL Server Data Tools** parmi les charges de travail affichées. Si vous ne voyez pas les objets de services de rapports dans la colonne centrale, ajoutez les extensions Reporting Services. Dans le menu **Outils** , sélectionnez **Extensions et mises à jour** > **En ligne** . Dans la colonne centrale, sélectionnez **Projets Microsoft Reporting Services** > **Télécharger** parmi les extensions affichées. Pour SSDT, consultez [Télécharger SSDT (SQL Server Data Tools)](../ssdt/download-sql-server-data-tools-ssdt.md). Dans Visual Studio 2019, si les étapes précédentes ne fonctionnaient pas, essayez d’installer [Extension de projet du service de rapport Microsoft](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio).


3. Sélectionnez l’icône **Projet Report Server** &nbsp;&nbsp;![ssrs_ssdt_report_server_project](media/ssrs-ssdt-report-server-project.png) &nbsp;&nbsp; dans la colonne centrale de la boîte de dialogue **Nouveau projet** .

4. Dans la zone de texte **Nom** , tapez « Tutorial » comme nom du projet. Par défaut, la zone de texte **Emplacement** affiche le chemin de votre dossier « Documents\Visual Studio 20xx\Projects\". Le Concepteur de rapports crée un dossier nommé Tutorial sous ce chemin, et crée le projet Tutorial dans ce dossier. Si le projet n’appartient pas à une solution VS, Visual Studio crée également un fichier solution (.sln).

5. Sélectionnez **OK** pour créer le projet. Le projet Tutorial s’affiche dans l’ **Explorateur de solutions** sur la droite.
  
## <a name="creating-a-report-definition-file-rdl"></a>Création d’un fichier de définition de rapport (RDL)  
  
1. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le dossier **Rapports** . Si vous ne voyez pas le volet **Explorateur de solutions** , sélectionnez le menu **Affichage** > **Explorateur de solutions** .

2. Sélectionnez **Ajouter** > **Nouvel élément** .

    ![Capture d’écran de l’Explorateur de solutions montrant l’option Rapports > Ajouter > Nouvel élément sélectionnée.](../reporting-services/media/ssrs-ssdt-add-report.png)

3. Dans la fenêtre **Ajouter un nouvel élément** , sélectionnez l’icône **Rapport** .

4. Tapez « Sales Orders.rdl » dans la zone de texte **Nom** .

5. Sélectionnez le **bouton Ajouter** en bas à droite de la boîte de dialogue **Ajouter un nouvel élément** pour terminer le processus. Le Concepteur de rapports s’ouvre et affiche le fichier de rapport Sales Orders en mode Conception.

    ![Capture d’écran de Visual Studio montrant le Concepteur de rapports et le rapport Commandes client en mode Création.](media/ssrs-ssdt-01-new-report-designer.png)

## <a name="next-steps"></a>Étapes suivantes

Jusqu’à présent, vous avez créé le projet de rapport Tutorial et le rapport Sales Orders. Dans les leçons suivantes, vous allez découvrir comment :

- Configurer une source de données pour le rapport.
- Créer un dataset à partir de la source de données.
- Concevoir et mettre en forme la disposition du rapport.

Poursuivez avec la [Leçon 2 : Spécification des informations de connexion &#40;Reporting Services&#41;](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md).
