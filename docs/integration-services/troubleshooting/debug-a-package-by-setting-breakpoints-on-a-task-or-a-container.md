---
title: "D&#233;boguer un package en d&#233;finissant des points d&#39;arr&#234;t sur une t&#226;che ou un conteneur | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conteneurs [Integration Services], points d’arrêt"
  - "points d'arrêt [Integration Services]"
  - "tâches [Integration Services], points d’arrêt"
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# D&#233;boguer un package en d&#233;finissant des points d&#39;arr&#234;t sur une t&#226;che ou un conteneur
  Cette section décrit la procédure de définition des points d'arrêt dans un package, une tâche, un conteneur de boucle For ou Foreach ou un conteneur de séquences.  
  
### Pour définir des points d'arrêt dans un package, une tâche ou un conteneur  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Double-cliquez sur le package dans lequel vous souhaitez définir des points d'arrêt.  
  
3.  Dans le concepteur SSIS, effectuez les opérations suivantes :  
  
    -   Pour définir des points d’arrêt dans l’objet package, cliquez sur l’onglet **Flux de contrôle**, placez le curseur n’importe où sur l’arrière-plan de l’aire de conception, cliquez avec le bouton droit, puis cliquez sur **Modifier les points d’arrêt**.  
  
    -   Pour définir des points d’arrêt dans un flux de contrôle de package, cliquez sur l’onglet **Flux de contrôle**, cliquez avec le bouton droit sur une tâche, un conteneur de boucle For ou Foreach ou un conteneur de séquences, puis cliquez sur **Modifier les points d’arrêt**.  
  
    -   Pour définir des points d’arrêt dans un gestionnaire d’événements, cliquez sur l’onglet **Gestionnaire d’événements**, cliquez avec le bouton droit sur une tâche, un conteneur de boucle For ou Foreach ou un conteneur de séquences, puis cliquez sur **Modifier les points d’arrêt**.  
  
4.  Dans la boîte de dialogue **Définir les points d’arrêt de \<nom_conteneur>**, sélectionnez les points d’arrêt à activer.  
  
5.  Vous pouvez également modifier le type du nombre d'accès et la valeur du nombre d'accès pour chaque point d'arrêt.  
  
6.  Pour enregistrer le package, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier**.  
  
## Voir aussi  
 [Outils de dépannage pour le développement des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Déboguer un script en définissant des points d'arrêt dans une tâche de script et un composant de script](../../integration-services/extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)   
 [Codage et débogage de la tâche de script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)   
 [Codage et débogage du composant Script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  