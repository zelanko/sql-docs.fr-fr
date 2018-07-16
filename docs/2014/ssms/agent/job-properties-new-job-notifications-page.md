---
title: 'Propriétés du travail : Nouveau travail (Page Notifications) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.notifications.f1
ms.assetid: ed393cbd-4496-4399-a177-e5baa92fb689
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 170456c9aeacb804a02d0e7450647b67453e635f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196769"
---
# <a name="job-properties-new-job-notifications-page"></a>Propriétés du travail : Nouveau travail (Page Notifications)
  Utilisez cette page pour définir des actions que l’Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devra exécuter une fois le travail terminé.  
  
## <a name="options"></a>Options  
 **Messagerie électronique**  
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
 [Implémenter des travaux](implement-jobs.md)   
 [Configurer la messagerie SQL Server Agent en vue d’utiliser la messagerie de base de données](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
  
