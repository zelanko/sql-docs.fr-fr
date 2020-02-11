---
title: Configurer le journal d’historique des travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 613c0ccae7be912bd3bec63905b838b7f07b59b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63033575"
---
# <a name="set-up-the-job-history-log"></a>Configurer le journal d'historique des travaux
  Cette rubrique décrit comment configurer le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] journal d’historique des travaux de l’agent.  
  
-   **Avant de commencer :**  [sécurité](#Security)  
  
-   **Pour configurer le journal d’historique des travaux à l’aide de :**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
 **Pour configurer le journal d’historique des travaux**  
  
1.  Dans l' [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] **Explorateur d’objets,** Connectez-vous à une instance du, puis développez cette instance.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de l'Agent SQL Server** , sélectionnez la page **Historique** .  
  
4.  Choisissez parmi les options suivantes :  
  
    1.  Activez la case à cocher **Limiter la taille de l'historique des travaux**, puis tapez le nombre maximal de lignes pour le journal de l'historique des travaux, ainsi que le nombre maximal de lignes par travail.  
  
    2.  Activez la case à cocher **Supprimer automatiquement l'historique de l'agent**, puis spécifiez une période de temps, de telle façon que l'historique antérieur à cette période soit purgé du journal.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter des travaux](implement-jobs.md)   
 [Surveiller l’activité des travaux](monitor-job-activity.md)   
 [Créer des travaux](create-jobs.md)  
  
  
