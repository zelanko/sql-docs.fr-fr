---
title: Redimensionner le journal d’historique des travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f1a8c9ab517d1f6a122144604d6b147e6f5eeaf6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762991"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log
  Cette rubrique explique comment définir des limites de taille pour les journaux d'historique des travaux de l'Agent [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour définir des limites de taille pour les journaux d'historique des travaux, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>Pour redimensionner le journal d'historique des travaux en fonction de sa taille brute  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et développez-la.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
3.  Sélectionnez la page **Historique** , puis vérifiez que la case **Limiter la taille du journal d’historique des travaux**est cochée.  
  
4.  Dans la zone **Taille maximale du journal d'historique des travaux** , entrez le nombre maximal de lignes autorisées dans le journal d'historique des travaux.  
  
5.  Dans la zone **Nombre maximal de lignes d'historique des travaux par travail** , entrez le nombre maximal de lignes d'historique des travaux autorisées pour un travail.  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>Pour redimensionner le journal d'historique des travaux en fonction du temps  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, puis cliquez sur **Propriétés**.  
  
3.  Sélectionnez la page **Historique** , puis cliquez sur **Supprimer automatiquement l'historique de l'agent**.  
  
4.  Sélectionnez le nombre approprié de **Jour(s)**, **Semaine(s)** ou **Mois(s)**.  
  
  
