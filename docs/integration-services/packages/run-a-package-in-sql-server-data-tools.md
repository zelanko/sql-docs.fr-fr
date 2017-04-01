---
title: "Ex&#233;cuter un package dans les outils de donn&#233;es SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages Integration Services, exécution"
  - "packages SSIS, exécution"
  - "packages [Integration Services], exécution"
  - "packages SQL Server Integration Services, exécution"
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
caps.latest.revision: 58
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# Ex&#233;cuter un package dans les outils de donn&#233;es SQL Server
  Les packages sont exécutés le plus souvent dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pendant le développement, le débogage et le test des packages. Quand vous exécutez un package à partir du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], il est exécuté immédiatement.  
  
 Pendant qu’un package s’exécute, le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] affiche la progression de l’exécution sous l’onglet **Progression**. Vous pouvez afficher l'heure de début et de fin du package et de ses tâches et conteneurs, ainsi que des informations sur les tâches et les conteneurs du package ayant échoué. Quand un package a terminé son exécution, les informations sur l’exécution restent disponibles sous l’onglet **Résultats d’exécution**. Pour plus d’informations, consultez la section « Rapport de progression » dans la rubrique [Débogage du flux de contrôle](../../integration-services/troubleshooting/debugging-control-flow.md).  
  
 **Déploiement au moment du design**. Lorsqu'un package est exécuté dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], il est créé, puis déployé dans un dossier. Avant d'exécuter le package, vous pouvez spécifier le dossier dans lequel il est déployé. Si vous ne spécifiez aucun dossier, le dossier **bin** est utilisé par défaut. Ce type de déploiement est appelé déploiement au moment de la conception.  
  
### Pour exécuter un package dans les outils de données SQL Server  
  
1.  Dans l’Explorateur de solutions, si votre solution contient plusieurs projets, cliquez avec le bouton droit sur le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient le package, puis cliquez sur **Définir en tant qu’objet de démarrage** pour définir le projet de démarrage.  
  
2.  Dans l’Explorateur de solutions, si votre projet contient plusieurs packages, cliquez avec le bouton droit sur un package, puis cliquez sur **Définir en tant qu’objet de démarrage** pour définir le package de démarrage.  
  
3.  Pour exécuter un package, utilisez l'une des procédures suivantes :  
  
    -   Ouvrez le package à exécuter, puis cliquez sur **Démarrer le débogage** dans la barre de menus ou appuyez sur F5. Une fois l'exécution du package terminée, appuyez sur Maj+F5 pour revenir au mode Création.  
  
    -   Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le package, puis cliquez sur **Exécuter le package**.  
  
### Pour spécifier un dossier différent pour le déploiement au moment du design  
  
1.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier de projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package à exécuter, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Pages de propriétés de \<nom de projet>**, cliquez sur **Générer**.  
  
3.  Mettez à jour la valeur de la propriété OutputPath pour indiquer le dossier que vous souhaitez utiliser pour le déploiement au moment du design, puis cliquez sur **OK**.  
  
## Voir aussi  
 [Exécution de projets et de packages](https://msdn.microsoft.com/library/hh213290.aspx)   
 [Packages Integration Services (SSIS)](https://msdn.microsoft.com/library/ms141134.aspx)  
  
  