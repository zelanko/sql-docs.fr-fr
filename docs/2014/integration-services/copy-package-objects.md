---
title: Copier des objets de packages | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 43378e9129b40324144a2f20f2039f6f376fa39d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200519"
---
# <a name="copy-package-objects"></a>Copier des objets de packages
  Cette rubrique indique comment copier des éléments de flux de contrôle, des éléments de flux de données, ainsi que des gestionnaires de connexions dans un package ou entre des packages.  
  
### <a name="to-copy-control-and-data-flow-items"></a>Pour copier des éléments de flux de contrôle et de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient les packages que vous voulez utiliser.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur les packages entre lesquels vous souhaitez effectuer une copie.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l’onglet du package qui contient les éléments à copier, puis cliquez sur l’onglet **Flux de contrôle**, **Flux de données**ou **Gestionnaires d’événements** .  
  
4.  Sélectionnez les éléments de flux de contrôle ou de flux de données à copier. Vous pouvez sélectionner des éléments un à la fois en appuyant sur la touche Maj et en cliquant sur l'élément, ou bien sélectionner des éléments en tant que groupe en faisant glisser le pointeur sur les éléments à sélectionner.  
  
    > [!IMPORTANT]  
    >  Les contraintes de précédence et les chemins d'accès qui connectent des éléments ne sont pas sélectionnés automatiquement lorsque vous sélectionnez les deux éléments qu'ils connectent. Pour copier un flux de travail ordonné (segment d'un flux de contrôle ou d'un flux de données), veillez à copier également les contraintes de priorité et les chemins d'accès.  
  
5.  Cliquez avec le bouton droit sur un élément sélectionné, puis cliquez sur **Copier**.  
  
6.  Dans le cas de copie d'éléments dans un package différent, cliquez sur le package de destination de la copie, puis cliquez sur l'onglet approprié pour le type d'élément.  
  
    > [!IMPORTANT]  
    >  Vous ne pouvez pas copier un flux de données dans un package tant que le package ne contient pas au moins une tâche de flux de données.  
  
7.  Cliquez avec le bouton droit, puis cliquez sur **Coller**.  
  
### <a name="to-copy-connection-managers"></a>Pour copier des gestionnaires de connexions  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package que vous voulez utiliser.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package.  
  
3.  Dans le concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] , cliquez sur l’onglet **Flux de contrôle**, **Flux de données**ou **Gestionnaire d’événements** .  
  
4.  Dans la zone **Gestionnaires de connexions** , cliquez avec le bouton droit sur le gestionnaire de connexions, puis cliquez sur **Copier**. Vous ne pouvez copier qu'un seul gestionnaire de connexions à la fois.  
  
5.  Si vous copiez des éléments dans un package différent, cliquez sur le package de destination de la copie, puis cliquez sur l’onglet **Flux de contrôle**, **Flux de données**ou **Gestionnaire d’événements** .  
  
6.  Cliquez avec le bouton droit sur **Gestionnaires de connexions** , puis cliquez sur **Coller**.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](control-flow/control-flow.md)   
 [Flux de données](data-flow/data-flow.md)   
 [Connexions Integration Services &#40;SSIS&#41;](connection-manager/integration-services-ssis-connections.md)   
 [Copier des éléments de projet](../../2014/integration-services/copy-project-items.md)  
  
  
