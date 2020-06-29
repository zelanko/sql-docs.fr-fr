---
title: 'Étape 1 : Copie du bundle de déploiement | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 624e5b98691f7f06878a10a3fa98f5f43615efd7
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440506"
---
# <a name="step-1-copying-the-deployment-bundle"></a>Étape 1 : Copier le bundle de déploiement
  Au cours de cette tâche, vous allez copier l'application de déploiement sur l'ordinateur de destination.  
  
 La méthode la plus simple pour copier l'application de déploiement sur l'ordinateur de destination est de commencer par créer un partage public, mapper un lecteur sur le partage public, puis copier l'application de déploiement sur le partage. Si vous n'êtes pas certain de la procédure à suivre pour créer et configurer des dossiers publics ou mapper des lecteurs, consultez la documentation Windows.  
  
### <a name="to-copy-the-deployment-bundle"></a>Pour copier l'application de déploiement  
  
1.  Accédez à l'application de déploiement sur votre ordinateur.  
  
     Si vous avez utilisé l'emplacement par défaut, l'application de déploiement correspond au dossier Bin\Deployment dans le dossier du didacticiel de déploiement.  
  
2.  Cliquez avec le bouton droit sur le dossier Deployment, puis cliquez sur **Copier**.  
  
3.  Accédez au partage public sur lequel vous souhaitez copier le dossier sur l'ordinateur cible et cliquez sur **Coller**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Exécution de l’Assistant Installation de package](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
![Icône de Integration Services (petite)](media/dts-16.gif "Icône Integration Services (petite)")  **restez à jour avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visiter la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
  
