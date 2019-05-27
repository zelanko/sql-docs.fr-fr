---
title: Ajouter, supprimer, modifier l’étendue de la Variable définie par l’utilisateur dans un Package | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], adding
ms.assetid: cbf40c7f-3c8a-48cd-aefa-8b37faf8b40e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 583e0f92f96c153fdeb0ade57fcdfa1d27578350
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66061984"
---
# <a name="add-delete-change-scope-of-user-defined-variable-in-a-package"></a>Ajouter, supprimer, modifier l'étendue de la variable définie par l'utilisateur dans un package
  Les procédures suivantes expliquent comment ajouter, supprimer et modifier l’étendue d’une variable définie par l’utilisateur dans un package, à l’aide de la fenêtre **Variables**.  
  
 Pour plus d’informations sur la portée des variables, consultez [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md).  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit également des variables système qui rendent disponibles les informations système au moment de l'exécution, pour être utilisées dans des conteneurs tels que des packages et des gestionnaires d'événements. Vous ne pouvez pas supprimer des variables système.  
  
### <a name="to-add-a-variable"></a>Pour ajouter une variable  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] que vous voulez utiliser.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , pour définir la portée de la variable, effectuez l'une des opérations suivantes :  
  
    -   Pour définir la portée du package, cliquez n’importe où sur l’aire de conception de l’onglet **Flux de contrôle** .  
  
    -   Pour définir la portée d’un gestionnaire d’événements, sélectionnez un exécutable et un gestionnaire d’événements sur l’aire de conception de l’onglet **Gestionnaire d’événements** .  
  
    -   Pour définir la portée d’une tâche ou d’un conteneur, cliquez sur une tâche ou un conteneur sur l’aire de conception de l’onglet **Flux de contrôle** ou de l’onglet **Gestionnaire d’événements** .  
  
4.  Dans le menu **SSIS** , cliquez sur **Variables**. Vous pouvez éventuellement afficher la fenêtre **Variables** en mappant la commande View.Variables avec une combinaison de clés de votre choix dans la page **Clavier** de la boîte de dialogue **Options** .  
  
5.  Dans la fenêtre **Variables** , cliquez sur l’icône **Ajouter une variable** . La nouvelle variable est ajoutée à la liste.  
  
6.  Dans la boîte de dialogue **Options de la grille** , sélectionnez des colonnes supplémentaires à afficher dans la boîte de dialogue **Options de la grille de variables** , puis cliquez sur **OK**.  
  
7.  Éventuellement, définissez les propriétés d'une variable. Pour plus d’informations, consultez [Définir les propriétés d’une variable définie par l’utilisateur](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md).  
  
8.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-delete-a-variable"></a>Pour supprimer une variable.  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le package pour l'ouvrir.  
  
3.  Dans le menu **SSIS** , cliquez sur **Variables**. Vous pouvez éventuellement afficher la fenêtre **Variables** en mappant la commande View.Variables avec une combinaison de clés de votre choix dans la page **Clavier** de la boîte de dialogue **Options** .  
  
4.  Sélectionnez la variable à supprimer, puis cliquez sur **Supprimer la variable**.  
  
     Si vous ne voyez pas la variable dans la fenêtre variables, cliquez sur **Options de la grille** puis sélectionnez **Afficher les variables de toutes les étendues**.  
  
5.  Si la boîte de dialogue **Confirmer la suppression des variables** apparaît, cliquez sur **Oui** pour confirmer.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-change-the-scope-of-a-variable"></a>Pour modifier l'étendue d'une variable  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le package pour l'ouvrir.  
  
3.  Dans le menu **SSIS** , cliquez sur **Variables**. Vous pouvez éventuellement afficher la fenêtre **Variables** en mappant la commande View.Variables avec une combinaison de clés de votre choix dans la page **Clavier** de la boîte de dialogue **Options** .  
  
4.  Sélectionnez la variable, puis cliquez sur **Déplacer la variable**.  
  
     Si vous ne voyez pas la variable dans la fenêtre variables, cliquez sur **Options de la grille** puis sélectionnez **Afficher les variables de toutes les étendues**.  
  
5.  Dans la boîte de dialogue **Sélectionner une nouvelle étendue** , sélectionnez le package ou un conteneur, une tâche ou un gestionnaire d'événements dans le package pour modifier l'étendue de la variable.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md)   
 [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)   
 [Définir les propriétés d’une Variable définie par l’utilisateur](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)   
 [Utiliser les valeurs des variables et des paramètres dans un package enfant](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
  
