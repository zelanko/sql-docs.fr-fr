---
title: "Propriétés du travail - Nouveau travail (page Notifications) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 41a11afd5d7f85c087198069311b033ad5a6116f
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="job-properties---new-job-notifications-page"></a>Propriétés du travail - Nouveau travail (page Notifications)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Utilisez cette page pour définir des actions que [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent devra exécuter une fois le travail terminé.  
  
## <a name="options"></a>Options  
**Courrier électronique**  
Sélectionnez cette option pour envoyer un courrier électronique lorsque le travail se termine. Choisissez ensuite l’opérateur qu’il faut avertir et la condition qui va déclencher la notification : **Lors de la réussite du travail**, **Lors de l’échec du travail**ou **Lorsque le travail est terminé**.  
  
**Radiomessagerie**  
Sélectionnez cette option pour envoyer un courrier électronique à un opérateur via la radiomessagerie lorsque le travail se termine. Spécifiez ensuite l’opérateur qu’il faut avertir et la condition qui va déclencher la notification : **Lors de la réussite du travail**, **Lors de l’échec du travail**ou **Lorsque le travail est terminé**.  
  
**Envoi réseau**  
Sélectionnez cette option pour avertir un opérateur de la fin du travail via l'envoi réseau. Spécifiez ensuite l’opérateur qu’il faut avertir et la condition qui va déclencher la notification : **Lors de la réussite du travail**, **Lors de l’échec du travail**ou **Lorsque le travail est terminé**.  
  
**Écrire dans le journal des événements des applications Windows**  
Sélectionnez cette option pour écrire une entrée dans le journal des événements des applications lorsque le travail est terminé. Choisissez ensuite la condition qui va déclencher l’écriture de l’entrée : **Lors de la réussite du travail**, **Lors de l’échec du travail**ou **Lorsque le travail est terminé**.  
  
**Supprimer le travail automatiquement**  
Sélectionnez cette option pour supprimer le travail une fois celui-ci terminé. Choisissez ensuite la condition qui va déclencher la suppression du travail : **Lors de la réussite du travail**, **Lors de l’échec du travail**ou **Lorsque le travail est terminé**.  
  
## <a name="see-also"></a>Voir aussi  
[Implémenter des travaux](../../ssms/agent/implement-jobs.md)  
[Procédure : configurer la messagerie de l'Agent SQL Server en vue de l'utilisation de la messagerie de base de données (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)  
  
