---
title: 'Étape 1 : Copie du bundle de déploiement | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: b6ef1e56-d278-4a24-afd3-68d8e0595cbb
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6078f133e8f14f570540ff02a9f107578c5fada1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086527"
---
# <a name="lesson-3-1---copying-the-deployment-bundle"></a>Leçon 3-1 : Copie du bundle de déploiement

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Au cours de cette tâche, vous allez copier l'application de déploiement sur l'ordinateur de destination.  
  
La méthode la plus simple pour copier l'application de déploiement sur l'ordinateur de destination est de commencer par créer un partage public, mapper un lecteur sur le partage public, puis copier l'application de déploiement sur le partage. Si vous n'êtes pas certain de la procédure à suivre pour créer et configurer des dossiers publics ou mapper des lecteurs, consultez la documentation Windows.  
  
### <a name="to-copy-the-deployment-bundle"></a>Pour copier l'application de déploiement  
  
1.  Accédez à l'application de déploiement sur votre ordinateur.  
  
    Si vous avez utilisé l'emplacement par défaut, l'application de déploiement correspond au dossier Bin\Deployment dans le dossier du didacticiel de déploiement.  
  
2.  Cliquez avec le bouton droit sur le dossier Deployment, puis cliquez sur **Copier**.  
  
3.  Accédez au partage public sur lequel vous souhaitez copier le dossier sur l'ordinateur cible et cliquez sur **Coller**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Étape 2 : Exécution de l'Assistant Installation de package](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
  
  
