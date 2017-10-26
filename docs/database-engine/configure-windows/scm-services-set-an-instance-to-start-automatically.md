---
title: "Services SCM - Définir le démarrage automatique d’une instance | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63598cfe81abc270430638d9d45a812ab2207815
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="scm-services---set-an-instance-to-start-automatically"></a>Services SCM - Définir le démarrage automatique d’une instance
  Cette rubrique explique comment définir une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin qu'elle démarre automatiquement dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration SQL Server. Durant l'installation, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est normalement configuré afin de démarrer automatiquement. Si le démarrage automatique n'a pas été configuré, vous pouvez modifier ce paramètre lorsque vous le souhaitez.  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a>Pour définir le démarrage automatique d'une instance de SQL Server  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
    > [!NOTE]  
    >  Étant donné que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant logiciel enfichable pour le programme [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console et non pas un programme autonome, le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’apparaît pas en tant qu’application dans les versions plus récentes de Windows.  
    >   
    >  -   **Windows 10**:  
    >          Pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dans la **page d’accueil**, tapez SQLServerManager13.msc (pour [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Pour les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , remplacez 13 par un nombre plus petit. Le fait de cliquer sur SQLServerManager13.msc ouvre le Gestionnaire de configuration. Pour épingler le Gestionnaire de configuration à la page d’accueil ou à la barre des tâches, cliquez avec le bouton droit sur SQLServerManager13.msc, puis cliquez sur **Ouvrir l’emplacement du fichier**. Dans l’Explorateur de fichiers Windows, cliquez avec le bouton droit sur SQLServerManager13.msc, puis cliquez sur **Épingler à l’écran d’accueil** ou **Épingler à la barre des tâches**.  
    > -   **Windows 8**:  
    >          Pour ouvrir le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sur l’icône **Rechercher**, sous **Applications**, tapez **SQLServerManager\<version>.msc**, par exemple **SQLServerManager13.msc**, puis appuyez sur **Entrée**.  
  
2.  Dans le **Gestionnaire de configuration SQL Server**, développez **Services**, puis cliquez sur **SQL Server**.  
  
3.  Dans le volet d’informations, cliquez avec le bouton droit sur le nom de l’instance qui devra démarrer automatiquement, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés de SQL Server \<***nom_instance***>**, définissez **Mode de démarrage** sur **Automatique**.  
  
5.  Cliquez sur **OK**, puis fermez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Empêcher le démarrage automatique d’une instance de SQL Server &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/scm-services-prevent-automatic-startup-of-an-instance.md)   
 [Se connecter à un autre ordinateur &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md)   
 [Configurer WMI pour afficher l’état du serveur dans les outils SQL Server](http://msdn.microsoft.com/library/7e97197b-ed4d-40d1-9a52-9ab1d92401d7)  
  
  

