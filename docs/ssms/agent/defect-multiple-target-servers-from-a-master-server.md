---
title: "Annuler l’inscription de plusieurs serveurs cibles dans un serveur maître | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e2c38be3173c025c9d4afccffe7660de8194a22
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a>Annuler l'inscription de plusieurs serveurs cibles dans un serveur maître
Cette rubrique explique comment annuler l'inscription de plusieurs serveurs cibles sur une configuration d'administration multiserveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. Exécutez la procédure suivante à partir du serveur maître :  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a>Pour annuler l'inscription de plusieurs serveurs cibles dans un serveur maître  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur configuré en tant que serveur maître.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Gérer les serveurs cibles**.  
  
3.  Cliquez sur **Publier les instructions**puis, dans la liste **Type d'instruction** , sélectionnez **Désinscrire**.  
  
4.  Sous **Destinataires**, activez l'une des options suivantes :  
  
    -   **Tous les serveurs cibles** pour annuler l'inscription de tous les serveurs cibles de ce serveur principal. Utilisez cette option si vous souhaitez désinstaller complètement la configuration de l'administration multiserveur active.  
  
    -   **Serveurs cibles sélectionnés**, puis cliquez sur la zone **Sélectionner** correspondante afin d'annuler l'inscription de certains serveurs cibles (mais pas tous) de ce serveur maître.  
  
## <a name="see-also"></a>Voir aussi  
[Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md)  
[Administration automatisée à l'échelle d'une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Annuler l'inscription d'un serveur cible dans un serveur maître](../../ssms/agent/defect-a-target-server-from-a-master-server.md)  
  
