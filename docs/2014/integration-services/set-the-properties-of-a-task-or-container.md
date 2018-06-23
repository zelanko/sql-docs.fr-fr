---
title: Définir les propriétés d’une tâche ou un conteneur | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tasks [Integration Services], properties
ms.assetid: 52d47ca4-fb8c-493d-8b2b-48bb269f859b
caps.latest.revision: 48
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 08133206f867492f52c5d89d67819d8f928eb8ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044519"
---
# <a name="set-the-properties-of-a-task-or-container"></a>Définir les propriétés d'une tâche ou d'un conteneur
  Vous pouvez définir la plupart des propriétés des tâches et des conteneurs à l’aide de la fenêtre **Propriétés**. Les seules exceptions sont les propriétés des collections de tâches et les propriétés trop complexes à définir dans la fenêtre **Propriétés** . Par exemple, vous ne pouvez pas configurer l’énumérateur utilisé par le conteneur de boucles Foreach dans la fenêtre **Propriétés** . Vous devez utiliser un éditeur de tâche ou de conteneur pour définir ces propriétés complexes. La plupart des éditeurs de tâche et de conteneur possèdent plusieurs nœuds contenant chacun des propriétés connexes. Le nom du nœud indique l'objet des propriétés contenues dans le nœud.  
  
 Les procédures suivantes décrivent comment définir les propriétés d’une tâche ou d’un conteneur en utilisant les fenêtres **Propriétés** ou l’éditeur de tâche ou de conteneur correspondant.  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-the-properties-window"></a>Pour définir les propriétés d'une tâche ou d'un conteneur à l'aide de la fenêtre Propriétés  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Sur l’aire de conception de l’onglet **Flux de contrôle** , cliquez avec le bouton droit sur la tâche ou le conteneur, puis cliquez sur **Propriétés**.  
  
5.  Dans la fenêtre **Propriétés** , mettez à jour la valeur de la propriété.  
  
    > [!NOTE]  
    >  Vous pouvez définir les propriétés en tapant une valeur directement dans la zone de texte ou en sélectionnant une valeur dans une liste. Néanmoins, certaines propriétés sont plus complexes et disposent d'un éditeur de propriétés personnalisées. Pour définir la propriété, cliquez dans la zone de texte, puis sur le bouton Générer **(…)** pour ouvrir l’éditeur personnalisé.  
  
6.  Si vous le souhaitez, créez des expressions de propriété afin de mettre à jour de manière dynamique les propriétés de la tâche ou du conteneur. Pour plus d’informations, consultez [Ajouter ou modifier une Expression de propriété](expressions/add-or-change-a-property-expression.md).  
  
7.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-set-the-properties-of-a-task-or-container-by-using-a-task-or-container-editor"></a>Pour définir les propriétés d'une tâche ou d'un conteneur à l'aide d'un éditeur de tâche ou de conteneur  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Sur l’aire de conception de l’onglet **Flux de contrôle** , cliquez avec le bouton droit sur la tâche ou le conteneur, puis cliquez sur **Modifier** pour ouvrir l’éditeur de tâche ou de conteneur correspondant.  
  
     Pour plus d’informations sur la configuration du conteneur de boucles For, consultez [Configurer un conteneur de boucles For](control-flow/for-loop-container.md).  
  
     Pour plus d’informations sur la configuration du conteneur de boucles Foreach, consultez [Configurer un conteneur de boucles Foreach](control-flow/foreach-loop-container.md).  
  
    > [!NOTE]  
    >  Le conteneur de séquences ne possède pas d'éditeur personnalisé.  
  
5.  Si l'éditeur de tâche ou de conteneur comporte plusieurs nœuds, cliquez sur celui qui contient la propriété à définir.  
  
6.  Si vous le souhaitez, cliquez sur **Expressions** , puis dans la page **Expressions** , créez des expressions de propriété afin de mettre à jour dynamiquement les propriétés de la tâche ou du conteneur. Pour plus d’informations, consultez [Ajouter ou modifier une Expression de propriété](expressions/add-or-change-a-property-expression.md).  
  
7.  Mettez à jour la valeur de la propriété.  
  
8.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches Integration Services](control-flow/integration-services-tasks.md)   
 [Conteneurs Integration Services](control-flow/integration-services-containers.md)  
  
  