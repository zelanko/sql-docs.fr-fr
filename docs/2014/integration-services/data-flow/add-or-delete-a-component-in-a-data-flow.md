---
title: Ajouter ou supprimer un composant dans un flux de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding components
- components [Integration Services], data flow
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5677fe0742c44924483b4e49b50e9746b6ed7449
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62832211"
---
# <a name="add-or-delete-a-component-in-a-data-flow"></a>Ajouter ou supprimer un composant dans un flux de données
  Les composants de flux de données sont des sources, des destinations et des transformations dans un flux de données. Pour que vous puissiez ajouter des composants à un flux de données, le flux de contrôle du package doit inclure une tâche de flux de données.  
  
 Les procédures ci-dessous montrent comment ajouter ou supprimer un composant dans le flux de données d'un package.  
  
### <a name="to-add-a-component-to-a-data-flow"></a>Pour ajouter un composant à un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données qui contient le flux de données auquel vous voulez ajouter un composant.  
  
4.  Dans la boîte à outils, développez **Sources de flux de données**, **Transformations du flux de données**ou **Destinations du flux de données**, puis faites glisser un élément de flux de données sur l’aire de conception de l’onglet **Flux de données** .  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### <a name="to-delete-a-component-from-a-data-flow"></a>Pour supprimer un composant d'un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données contenant le flux de données duquel vous voulez supprimer un composant.  
  
4.  Cliquez avec le bouton droit sur le composant du flux de données, puis cliquez sur **Supprimer**.  
  
5.  Confirmez la suppression.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Connecter des composants dans un flux de données](data-flow.md)   
 [Configurer une sortie d’erreur dans un composant de transmission de données](../configure-an-error-output-in-a-data-flow-component.md)   
 [Flux de données](data-flow.md)  
  
  
