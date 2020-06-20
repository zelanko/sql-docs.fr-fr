---
title: Connecter des composants dans un flux de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ea5c088bf16576cf6711e9f01ee21452dd001b8e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84916469"
---
# <a name="connect-components-in-a-data-flow"></a>Connecter des composants dans un flux de données
  Cette procédure décrit comment connecter la sortie de composants d'un flux de données à d'autres composants du même flux de données.  
  
### <a name="to-connect-components-in-a-data-flow"></a>Pour connecter des composants dans un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données qui contient le flux de données dans lequel vous voulez connecter des composants.  
  
4.  Dans l’aire de conception de l’onglet **Flux de données** , sélectionnez la transformation ou la source à connecter.  
  
5.  Faites glisser la flèche de sortie verte d'une transformation ou d'une source vers une transformation ou une destination. Certains composants de flux de données comportent des sorties d'erreurs, que vous pouvez connecter de la même manière.  
  
    > [!NOTE]  
    >  Certains composants de flux de données peuvent avoir plusieurs sorties. Vous pouvez connecter chaque sortie à une transformation ou une destination différente.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter ou supprimer un composant dans un Workflow](data-flow.md)   
 [Configurer une sortie d’erreur dans un composant de transmission de données](../configure-an-error-output-in-a-data-flow-component.md)   
 [Flux de données](data-flow.md)  
  
  
