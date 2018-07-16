---
title: Utiliser les valeurs des Variables et des paramètres dans un Package enfant | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], passing between packages
- configurations [Integration Services]
- packages [Integration Services], configurations
- variables [Integration Services], adding
ms.assetid: 9b939edb-4e17-48e5-8428-855beb10049c
caps.latest.revision: 18
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f1c522a87bfd20608d1e42080ad9ff3d3ae10973
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287515"
---
# <a name="use-the-values-of-variables-and-parameters-in-a-child-package"></a>Utiliser les valeurs des variables et des paramètres dans un package enfant
  Cette procédure explique comment créer une configuration de package qui utilise le type de configuration de variable parent. Ce type de configuration active un package enfant exécuté à partir d'un package parent pour accéder à une variable dans le parent.  
  
> [!NOTE]  
>  Vous pouvez également passer les valeurs à un package enfant en configurant la tâche d'exécution afin de mapper les variables ou paramètres du package parent, ou les paramètres du projet, aux paramètres du package enfant. Pour plus d’informations, consultez [Tâche d’exécution de package](control-flow/execute-package-task.md).  
  
 Il n'est pas nécessaire de créer la variable dans le package parent avant de créer la configuration de package dans le package enfant. Vous pouvez ajouter la variable au package parent à tout moment, mais vous devez utiliser le nom exact de la variable parent dans la configuration du package. Cependant, avant que vous puissiez créer une configuration de variable parent, la configuration doit pouvoir mettre à jour une variable existante dans le package enfant. Pour plus d’informations sur l’ajout et la configuration de variables, consultez [Ajouter, supprimer, modifier l’étendue de la variable définie par l’utilisateur dans un package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).  
  
 La portée de la variable dans le package parent utilisé dans une configuration de variable parent peut être définie à la tâche d'exécution de package, au conteneur qui détient la tâche ou au package. Si plusieurs variables portant le même nom sont définies dans un package, la variable la plus proche en portée de la tâche d'exécution de package est employée. La portée la plus proche de la tâche d'exécution de package est la tâche proprement dite.  
  
### <a name="to-add-a-variable-to-a-parent-package"></a>Pour ajouter une variable à un package parent  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package auquel vous voulez ajouter une variable à transmettre à un package enfant.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , pour définir la portée de la variable, effectuez l'une des opérations suivantes :  
  
    -   Pour définir la portée du package, cliquez n’importe où sur l’aire de conception de l’onglet **Flux de contrôle** .  
  
    -   Pour définir la portée à un conteneur parent de la tâche d'exécution de package, cliquez sur le conteneur.  
  
    -   Pour définir la portée de la tâche d'exécution de package, cliquez sur la tâche.  
  
4.  Ajoutez et configurez une variable.  
  
    > [!NOTE]  
    >  Sélectionnez un type de données compatible avec les données que la variable stockera.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-add-a-variable-to-a-child-package"></a>Pour ajouter une variable à un package enfant  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package auquel vous souhaitez ajouter une configuration de variable parent.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , pour définir la portée au package, cliquez n’importe où sur la zone de conception de l’onglet **Flux de contrôle** .  
  
4.  Ajoutez et configurez une variable.  
  
    > [!NOTE]  
    >  Sélectionnez un type de données compatible avec les données que la variable stockera.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-add-a-parent-package-configuration-to-a-child-package"></a>Pour ajouter une configuration de package parent à un package enfant  
  
1.  S’il n’est pas déjà ouvert, ouvrez le package enfant dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez dans la zone de conception de l’onglet **Flux de contrôle** .  
  
3.  Dans le menu **SSIS** , cliquez sur **Configurations du package**.  
  
4.  Dans la boîte de dialogue **Bibliothèque des configurations du package** , sélectionnez **Activer les configurations du package**et cliquez sur **Ajouter**.  
  
5.  Dans la page Assistant Configuration de package, cliquez sur **Suivant**.  
  
6.  Dans la page Sélectionner le type de configuration, dans la liste **Type de configuration** , sélectionnez **Variable de package parent** et effectuez l’une des interventions suivantes :  
  
    -   Sélectionnez **Spécifier directement les paramètres de configuration**, et dans la zone **Variable parent** , fournissez le nom de la variable dans le package parent à utiliser dans la configuration.  
  
        > [!IMPORTANT]  
        >  Les noms des variables tiennent compte de la casse.  
  
    -   Sélectionnez **L’emplacement de la configuration est stocké dans une variable d’environnement** , puis dans la **liste Variable d’environnement**, sélectionnez la variable d’environnement qui contient le nom de la variable.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Dans la page Sélectionner la propriété cible, développez le nœud **Variable** , puis développez le nœud **Propriétés** de la variable à configurer, puis cliquez sur la propriété devant être définie par la configuration.  
  
9. Cliquez sur **Suivant**.  
  
10. Dans la page Fin de l'Assistant, modifiez facultativement le nom par défaut de la configuration, puis vérifiez les informations de configuration.  
  
11. Cliquez sur **Terminer** pour mettre fin à l’Assistant et revenir à la boîte de dialogue **Bibliothèque des configurations du package** .  
  
12. Dans la boîte de dialogue **Bibliothèque des configurations du package** , la zone **Configuration** présente la nouvelle configuration.  
  
13. Cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurations de package](../../2014/integration-services/package-configurations.md)   
 [Créer des Configurations de Package](../../2014/integration-services/create-package-configurations.md)   
 [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)   
 [Utiliser des variables dans des packages](../../2014/integration-services/use-variables-in-packages.md)  
  
  
