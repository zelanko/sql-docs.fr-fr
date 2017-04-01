---
title: "Configurer des points de contr&#244;le pour red&#233;marrer un package ayant &#233;chou&#233; | Microsoft Docs"
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
  - "points de contrôle [Integration Services]"
  - "redémarrage de packages"
  - "démarrage de packages"
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Configurer des points de contr&#244;le pour red&#233;marrer un package ayant &#233;chou&#233;
  Vous pouvez configurer les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de sorte qu'ils redémarrent à partir d'un point d'arrêt au lieu de réexécuter l'ensemble du package. Pour ce faire, vous devez définir les propriétés des points de contrôle.  
  
### Pour configurer le redémarrage d'un package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package à configurer.  
  
2.  Dans **l’Explorateur de solutions**, double-cliquez sur le package pour l’ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de contrôle** .  
  
4.  Cliquez avec le bouton droit n’importe où dans l’arrière-plan de la surface de dessin du flux de contrôle, puis cliquez sur **Propriétés**.  
  
5.  Définissez la propriété SaveCheckpoints sur **True**.  
  
6.  Tapez le nom du fichier point de contrôle dans la propriété CheckpointFileName.  
  
7.  Définissez la propriété CheckpointUsage sur l’une des deux valeurs suivantes :  
  
    -   Sélectionnez **Always** pour toujours redémarrer le package à partir du point d'arrêt.  
  
        > [!IMPORTANT]  
        >  Une erreur se produit si le fichier de point d'arrêt n'est pas disponible.  
  
    -   Sélectionnez **IfExists** pour redémarrer le package uniquement si le fichier de point d'arrêt est disponible.  
  
8.  Configurez les tâches et les conteneurs à partir desquels le package peut redémarrer.  
  
    -   Cliquez avec le bouton droit sur une tâche ou un conteneur, puis cliquez sur **Propriétés**.  
  
    -   Affectez à la propriété FailPackageOnFailure la valeur **True** pour chaque tâche et conteneur sélectionnés.  
  
## Voir aussi  
 [Redémarrer des packages à l'aide de points de contrôle](../../integration-services/packages/restart-packages-by-using-checkpoints.md)  
  
  