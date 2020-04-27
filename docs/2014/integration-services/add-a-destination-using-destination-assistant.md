---
title: Ajouter une destination à l’aide de l’Assistant destination | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 747a0de0-3c2f-4d31-a692-7111fc0911d8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 66e48903776824b0e540b854a5704ceef3a9782e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062068"
---
# <a name="add-a-destination-using-destination-assistant"></a>Ajouter une destination à l'aide de l'Assistant Destination
  Cette rubrique indique les étapes à suivre pour ajouter une nouvelle destination via l’Assistant Destination. En outre, elle recense les options disponibles dans la boîte de dialogue **Ajouter une nouvelle destination** , qui s’affiche quand vous effectuez un glisser-déplacer de l’Assistant Destination vers le concepteur SSIS.  
  
### <a name="to-use-destination-assistant-to-add-a-destination"></a>Pour utiliser l'Assistant Destination afin d'ajouter une destination  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] auquel vous voulez ajouter un composant destination.  
  
2.  Faites glisser le composant **Assistant destination** de la boîte à outils SSIS vers l’onglet **Flow Data** . La boîte de dialogue **Ajouter une nouvelle destination** doit s’afficher. La section suivante fournit des détails sur les options disponibles dans la boîte de dialogue.  
  
3.  Sélectionnez le type de la destination dans la liste **Types** .  
  
4.  Sélectionnez un gestionnaire de connexions existant dans la liste **Gestionnaires de connexions** ou sélectionnez **\<Nouveau>** pour en créer un.  
  
5.  Si vous sélectionnez un gestionnaire de connexions existant, cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une nouvelle destination** . Vous devez constater que la destination et les gestionnaires de connexions ont été ajoutés au flux de données.  
  
6.  Si vous cliquez sur ** \<nouveau>** pour créer un gestionnaire de connexions, vous devez voir s’afficher une boîte de dialogue **Gestionnaire de connexions** , qui vous permet de spécifier des paramètres pour la connexion. Une fois que vous avez fini de créer le gestionnaire de connexions, vous constatez que la destination et le gestionnaire de connexions figurent dans le concepteur SSIS.  
  
  
