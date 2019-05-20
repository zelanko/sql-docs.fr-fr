---
title: Connecter des composants dans un flux de données | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8d353876938b3e64317f461240b2333e71217449
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65727124"
---
# <a name="connect-components-in-a-data-flow"></a>Connecter des composants dans un flux de données

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Cette procédure décrit comment connecter la sortie de composants d'un flux de données à d'autres composants du même flux de données.  
Le flux de données d’un package est construit sur la surface de conception de l’onglet **Flux de données** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Si un flux de données contient deux composants de flux de données, vous pouvez les relier en connectant la sortie d'une source ou d'une transformation à l'entrée d'une transformation ou d'une destination. Le connecteur entre ces deux composants de flux de données porte le nom de chemin d'accès.  
  
 Le diagramme qui suit montre un flux de données simple formé d'un composant source, de deux transformations, d'un composant de destination et des chemins d'accès les connectant.  
  
 ![Data flow](../../integration-services/data-flow/media/mw-dts-08.gif "Data flow")  
  
 Une fois deux composants connectés, vous pouvez afficher les métadonnées des données empruntant le chemin et les propriétés du chemin dans **l’Éditeur du chemin d’accès au flux de données**. Pour plus d’informations, consultez [Chemins d’accès d’Integration Services](../../integration-services/data-flow/integration-services-paths.md).  
  
 Vous pouvez également ajouter des visionneuses de données aux chemins d'accès. Une visionneuse de données permet d'afficher les données circulant entre les composants du flux de données lors de l'exécution du package.  
  
### <a name="connect-components-in-a-data-flow"></a>Connecter des composants dans un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle** , puis double-cliquez sur la tâche de flux de données qui contient le flux de données dans lequel vous voulez connecter des composants.  
  
4.  Dans l’aire de conception de l’onglet **Flux de données** , sélectionnez la transformation ou la source à connecter.  
  
5.  Faites glisser la flèche de sortie verte d'une transformation ou d'une source vers une transformation ou une destination. Certains composants de flux de données comportent des sorties d'erreurs, que vous pouvez connecter de la même manière.  
  
    > [!NOTE]  
    >  Certains composants de flux de données peuvent avoir plusieurs sorties. Vous pouvez connecter chaque sortie à une transformation ou une destination différente.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a> Voir aussi  
 [Ajouter ou supprimer un composant dans un flux de données](../../integration-services/data-flow/add-or-delete-a-component-in-a-data-flow.md)   
 [Débogage d’un flux de données](../../integration-services/troubleshooting/debugging-data-flow.md) [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  
