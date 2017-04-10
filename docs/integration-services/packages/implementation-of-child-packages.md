---
title: "Impl&#233;mentation de packages enfants | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages enfants"
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Impl&#233;mentation de packages enfants
  Quand vous implémentez un équilibrage de charge avec [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], des packages enfants sont installés sur d’autres serveurs pour tirer parti du temps UC ou serveur disponible. Pour créer et exécuter les packages enfants, les opérations suivantes sont nécessaires :  
  
-   Conception des packages enfants.  
  
-   Déplacement des packages sur le serveur distant.  
  
-   Création d'un travail de SQL Server Agent sur le serveur distant qui contient une étape exécutant le package enfant.  
  
-   Test et débogage du travail de SQL Server Agent et des packages enfants.  
  
 Lorsque vous concevez les packages enfants, les packages n'ont pas de limites dans leur conception, et vous pouvez inclure toutes les fonctionnalités souhaitées. Cependant, si le package accède à des données, vous devez vous assurer que le serveur qui exécute le package a accès aux données.  
  
 Pour identifier le package parent qui exécute les packages enfants, dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez avec le bouton droit sur le package dans l’Explorateur de solutions et sélectionnez **Package de point d’entrée**.  
  
 Une fois que les packages enfants ont été conçus, l'étape suivante consiste à les déployer sur les serveurs distants.  
  
## Déplacement du package enfant sur le serveur distant.  
 Il existe plusieurs façons de déplacer des packages sur d'autres serveurs. Les deux méthodes suggérées sont les suivantes :  
  
-   Exportation des packages à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   Déploiement de packages en créant un utilitaire de déploiement pour le projet qui contient les packages que vous voulez déployer, puis en exécutant l'Assistant Installation de package pour installer les packages sur le système de fichiers ou sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Déploiement de packages hérités &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
 Vous devez recommencer le déploiement sur chaque serveur distant à utiliser.  
  
## Création des travaux de SQL Server Agent  
 Une fois que les packages enfants ont été déployés sur les divers serveurs, créez un travail de SQL Server Agent sur chaque serveur contenant un package enfant. Le travail de SQL Server Agent contient une étape qui exécute le package enfant lors de l'appel de l'agent du travail. Les travaux de SQL Server Agent ne sont pas des travaux planifiés ; ils exécutent les packages enfants uniquement lorsqu'ils sont appelés par le package parent. La notification de la réussite ou de l'échec du travail au package parent reflète la réussite ou l'échec du travail de SQL Server Agent et l'aboutissement de son appel, et non la réussite ou l'échec du package enfant ou son éventuelle exécution.  
  
## Débogage des travaux de SQL Server Agent et des packages enfants.  
 Vous pouvez tester les travaux de SQL Server Agent et leurs packages enfants à l'aide de l'une des méthodes suivantes :  
  
-   Exécution de chaque package enfant dans le concepteur SSIS, en cliquant sur **Déboguer** / **Exécuter sans débogage**.  
  
-   Exécution du travail individuel de SQL Server Agent sur l’ordinateur distant à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], pour vérifier que le package fonctionne.  
  
 Pour plus d’informations sur la résolution des problèmes liés aux packages que vous exécutez à partir des travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consultez [Un package SSIS ne s’exécute pas lorsque vous appelez le package SSIS à partir d’une étape de travail de SQL Server Agent](http://support.microsoft.com/kb/918760) dans la Base de connaissances du support technique [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 SQL Server Agent vérifie l'accès au sous-système pour un proxy et donne accès au proxy à chaque exécution de l'étape de travail.  
  
 Vous pouvez créer un proxy dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## Tâches associées  
  
-   [Exécuter un package sur le serveur SSIS à l'aide de SQL Server Management Studio](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  