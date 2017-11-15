---
title: "Forcer l’interrogation d’un serveur maître par un serveur cible | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ae09299dd054f21263d746a2c39ae3c6e490e332
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>Forcer l'interrogation d'un serveur maître par un serveur cible
Cette rubrique explique comment forcer l'interrogation du serveur maître par un serveur cible. Le serveur cible doit être un serveur inscrit sur le serveur maître.  
  
Un travail est une série d'actions exécutées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Un travail multiserveur est un travail exécuté par un serveur maître sur un ou plusieurs serveurs cibles. Chaque serveur cible peut exécuter une instance du même travail au même moment. Chaque serveur cible interroge régulièrement le serveur maître, télécharge une copie des nouveaux travaux affectés au serveur cible, puis se déconnecte. Le serveur cible exécute localement le travail, puis se reconnecte au serveur maître pour charger l'état de la sortie du travail.  
  
> [!NOTE]  
> Si le serveur maître est accessible lorsque le serveur cible tente de charger l'état du travail, ce dernier est mis en attente dans le spouleur jusqu'à ce que le serveur maître soit accessible.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#Restrictions), [Sécurité](#Security)  
  
-   **Pour forcer l’interrogation du serveur maître par un serveur cible, avec :** [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
Le serveur cible doit être un serveur inscrit sur le serveur maître. Vous devez exécuter les instructions fournies dans cette rubrique à partir du serveur maître.  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md) et [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
**Pour forcer l'interrogation d'un serveur maître par un serveur cible**  
  
1.  Dans l' **Explorateur d'objets**, développez le serveur maître.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Gérer les serveurs cibles**.  
  
3.  Cliquez sur un serveur cible, puis sur **Forcer l'interrogation**.  
  
