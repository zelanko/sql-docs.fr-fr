---
title: Configurer WMI pour afficher l’état du serveur dans les outils SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cf6e46865e2cd9c65a7694d7c32cbcc1bd9cbc21
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177122"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Configurer WMI pour afficher l'état du serveur dans les outils SQL Server
  Cette rubrique explique comment configurer WMI pour afficher l'état du serveur dans les outils SQL Server dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Lors de la connexion aux serveurs, les composants Serveurs inscrits et Explorateur d'objets de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], ainsi que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , utilisent WMI (Windows Management Instrumentation) pour obtenir l'état des services [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent (MSSQLSERVER). Pour afficher l'état du service, l'utilisateur doit disposer des droits d'accéder à distance à l'objet WMI. Cette autorisation peut être configurée seulement si WMI a été installé sur le serveur.  
  
##  <a name="SSMSProcedure"></a> Pour configurer les autorisations WMI  
  
1.  Sur le serveur distant, dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **Open** zone, tapez `wmimgmt.msc`, puis cliquez sur **OK**.  
  
3.  Dans le programme **Windows Management Infrastructure** , cliquez avec le bouton droit sur **Contrôle WMI (local)**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de WMI Control (Local)** , sous l’onglet **Sécurité** , développez **Root**, puis cliquez sur **CIMV2**.  
  
5.  Cliquez sur **Sécurité** pour ouvrir la boîte de dialogue **Sécurité pour ROOT\CIMV2** .  
  
6.  Ajoutez un groupe ou un utilisateur à la zone **Noms de groupes ou d’utilisateurs** et sélectionnez-le.  
  
7.  Dans le **autorisations pour ***\<groupe ou utilisateur >* boîte, sélectionnez le **autoriser** colonne, pour le **appel à distance autorisé** autorisation, pour les utilisateurs auxquels vous souhaitez à distance détecter l’état du service.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer, arrêter ou suspendre le service SQL Server Agent](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
