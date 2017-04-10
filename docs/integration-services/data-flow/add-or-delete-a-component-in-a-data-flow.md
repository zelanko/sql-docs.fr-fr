---
title: "Ajouter ou supprimer un composant dans un flux de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ajout de composants"
  - "composants [Integration Services], flux de données"
ms.assetid: d99124f9-0994-4f40-a48e-fdca6a4383e7
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Ajouter ou supprimer un composant dans un flux de donn&#233;es
  Les composants de flux de données sont des sources, des destinations et des transformations dans un flux de données. Pour que vous puissiez ajouter des composants à un flux de données, le flux de contrôle du package doit inclure une tâche de flux de données.  
  
 Les procédures ci-dessous montrent comment ajouter ou supprimer un composant dans le flux de données d'un package.  
  
### Pour ajouter un composant à un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle**, puis double-cliquez sur la tâche de flux de données qui contient le flux de données auquel vous voulez ajouter un composant.  
  
4.  Dans la boîte à outils, développez **Sources de flux de données**, **Transformations du flux de données** ou **Destinations du flux de données**, puis faites glisser un élément de flux de données sur l’aire de conception de l’onglet **Flux de données**.  
  
5.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
### Pour supprimer un composant d'un flux de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de contrôle**, puis double-cliquez sur la tâche de flux de données contenant le flux de données duquel vous voulez supprimer un composant.  
  
4.  Cliquez avec le bouton droit sur le composant du flux de données, puis cliquez sur **Supprimer**.  
  
5.  Confirmez la suppression.  
  
6.  Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## Voir aussi  
 [Connecter des composants dans un flux de données](../../integration-services/data-flow/connect-components-in-a-data-flow.md)   
 [Configurer une sortie d'erreur dans un composant de flux de données](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)   
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  