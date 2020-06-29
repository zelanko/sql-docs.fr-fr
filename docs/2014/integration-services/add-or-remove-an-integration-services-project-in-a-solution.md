---
title: Ajouter ou supprimer un projet Integration Services dans une solution | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 29f64f915f241ec274cf4a7babdf9937fe6c4131
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439626"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a>Ajouter ou supprimer un projet Integration Services dans une solution
  Les procédures suivantes décrivent comment ajouter ou supprimer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans une solution.  
  
 Vous pouvez uniquement ajouter un projet à une solution existante ou supprimer un projet d'une solution, lorsque la solution est visible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Si vous avez sélectionné l’option **toujours afficher la solution** dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] affiche une solution même lorsque cette solution contient un seul projet. Dans le cas contraire, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] affiche une solution uniquement lorsque cette solution contient plusieurs projets. Les projets supplémentaires peuvent être des projets [!INCLUDE[ssIS](../includes/ssis-md.md)] ou des projets d'autres types.  
  
## <a name="adding-an-integration-services-project"></a>Ajout d'un projet Integration Services  
 Quand vous ajoutez un projet, vous pouvez créer un nouveau projet vide dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou ajouter un projet que vous avez déjà créé pour une autre solution. Vous pouvez uniquement ajouter un projet à une solution existante quand la solution est visible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a>Pour ajouter un nouveau projet Integration Services à une solution  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez la solution à laquelle vous souhaitez ajouter un nouveau projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] et effectuez l'une des opérations suivantes :  
  
    -   Cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis sur **Nouveau projet**.  
  
    -   Dans le menu **Fichier** , pointez sur **Ajouter**, puis cliquez sur **Nouveau projet**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouveau projet** , dans le volet **Modèles** , cliquez sur **Projet Integration Services** .  
  
3.  Éventuellement, modifiez le nom et l'emplacement du projet.  
  
4.  Cliquez sur **OK**.  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a>Pour ajouter un projet Integration Services existant à une solution  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez la solution à laquelle vous souhaitez ajouter un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] existant, puis effectuez l'une des opérations suivantes :  
  
    -   Cliquez avec le bouton droit sur la solution, pointez sur **Ajouter**, puis cliquez sur **Projet existant**.  
  
    -   Dans le menu **Fichier** , cliquez sur **Ajouter**, puis sur **Projet existant**.  
  
2.  Dans la boîte de dialogue **Ajouter un projet existant** , recherchez le projet à ajouter, puis cliquez sur **Ouvrir**.  
  
3.  Le projet est ajouté au dossier de la solution dans l' **Explorateur de solutions**.  
  
## <a name="removing-an-integration-services-project"></a>Suppression d'un projet Integration Services  
 Vous ne pouvez supprimer un projet d'une solution que lorsque la solution est visible dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Une fois que la solution est visible, vous pouvez tout supprimer mais devez conserver un projet. Lorsqu'il ne reste qu'un seul projet, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] n'affiche plus le dossier des solutions et vous ne pouvez pas supprimer le dernier projet.  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a>Pour supprimer un projet Integration Services d'une solution  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez la solution dans laquelle vous souhaitez supprimer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis cliquez sur **Décharger le projet**.  
  
3.  Cliquez sur **OK** pour confirmer la suppression.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services &#40;projets de&#41; SSIS](integration-services-ssis-projects-and-solutions.md)   
 [Créer un projet Integration Services](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
