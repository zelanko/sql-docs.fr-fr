---
title: 'Étape 2 : Création du projet de déploiement | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6f5b0cc2c86ef483a7e2b2c0f5dccba21383641f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62891846"
---
# <a name="step-2-creating-the-deployment-project"></a>Étape 2 : création du projet de déploiement
  Dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], l'unité déployable est un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Avant de pouvoir déployer les packages, vous devez créer un nouveau projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et ajouter à ce projet tous les packages et les fichiers annexes que vous souhaitez déployer avec les packages.  
  
### <a name="to-create-the-integration-services-project"></a>Pour créer le projet Integration Services  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur **Microsoft SQL Server**, puis cliquez sur **SQL Server SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet** pour créer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  Dans la boîte de dialogue **Nouveau projet** , sélectionnez **Projet Integration Services** dans le volet **Modèles** .  
  
4.  Dans la zone **Nom** , remplacez le nom par défaut par **Didacticiel de déploiement**. Vous pouvez éventuellement désactiver la case à cocher **Créer le répertoire pour la solution** .  
  
5.  Acceptez l’emplacement par défaut ou cliquez sur **Parcourir** pour accéder au dossier que vous souhaitez utiliser.  
  
6.  Dans la boîte de dialogue **Emplacement du projet** , cliquez sur le dossier, puis sur **Ouvrir**.  
  
7.  Cliquez sur **OK**.  
  
8.  Par défaut, un package vide, nommé Package.dtsx, est créé et ajouté à votre projet. Cependant, vous ne pourrez pas utiliser ce package ; à la place, vous allez ajouter des packages existants au projet. Dans la mesure où tous les packages d'un projet sont inclus dans le déploiement, vous devez supprimer le fichier Package.dtsx. Pour ce faire, cliquez dessus avec le bouton droit, puis cliquez sur **Supprimer**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 3 : Ajout de packages et d’autres fichiers](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
![Icône de Integration Services (petite)](media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Projets Integration Services &#40;SSIS&#41;](integration-services-ssis-projects-and-solutions.md)  
  
  
