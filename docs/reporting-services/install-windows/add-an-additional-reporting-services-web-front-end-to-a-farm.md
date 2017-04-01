---
title: "Ajouter un serveur Web frontal Reporting Services suppl&#233;mentaire &#224; une batterie | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7a11bda-ae26-49ac-b071-37d83cae5afe
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 11
---
# Ajouter un serveur Web frontal Reporting Services suppl&#233;mentaire &#224; une batterie
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le mode SharePoint inclut les composants nécessaires pour les serveurs d’applications et les serveurs web frontaux. Cette rubrique traite de l'installation des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requis pour un serveur Web frontal, y compris les pages d'application utilisées par les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] telles que les abonnements, les alertes de données et [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. L’installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] principale nécessaire pour un serveur web frontal consiste à installer le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint 2016.  
  
## Conditions préalables  
  
-   Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.  
  
-   L'ordinateur doit être attaché à un domaine.  
  
-   Vous devez connaître le nom du serveur de base de données existant qui héberge la configuration et les bases de données de contenu SharePoint.  
  
-   Le serveur de base de données doit être configuré pour autoriser les connexions de base de données distantes.  S'il ne l'est pas, vous ne pourrez pas joindre le nouveau serveur à la batterie car il ne pourra pas établir de connexion aux bases de données de configuration SharePoint.  
  
-   Le nouveau serveur devra avoir la même version de SharePoint installée que celle exécutée par les serveurs de batterie actuels. Par exemple, si SharePoint 2013 Service Pack 1 (SP1) est déjà installé sur la batterie de serveurs, vous devez installer aussi le SP1 sur le nouveau serveur pour qu’il puisse rejoindre la batterie de serveurs.  
  
## Étapes  
 Les étapes de cette rubrique partent du principe qu'un administrateur de batterie de serveurs SharePoint installe et configure le serveur. Le diagramme illustre un environnement à trois niveaux classique et les éléments numérotés sont décrits dans la liste suivante :  
  
-   (1) Plusieurs serveurs Web frontaux. Les serveurs Web frontaux ont besoin du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint 2010. Les étapes suivantes ajoutent un deuxième serveur d'applications à cette couche.  
  
-   (2) Deux serveurs d'applications exécutant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et des sites Web, par exemple Administration centrale.  
  
-   (3) Deux serveurs de base de données SQL Server.  
  
-   (4) Représente une solution d'équilibrage de la charge réseau matérielle ou logicielle  
  
 ![Add SSRS to a new SharePoint WFE](../../reporting-services/install-windows/media/rs-sharepointscale-wfe.gif "Add SSRS to a new SharePoint WFE")  
  
 Les étapes suivantes impliquent qu'un administrateur procède à l'installation et à la configuration du serveur.  
  
|Étape|Description et lien|  
|----------|--------------------------|  
|Ajoutez un serveur SharePoint à une batterie de serveurs.|Vous devez installer SharePoint pour déployer une autre application Reporting Services.<br/><br/>Pour SharePoint 2013, consultez [Ajouter un serveur SharePoint à une batterie de serveurs dans SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx).<br/><br/>Pour SharePoint 2016, consultez [Ajouter un serveur SharePoint à une batterie de serveurs dans SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx).|  
|Installez le complément [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint 2016.|Il existe plusieurs méthodes pour installer le complément. Les étapes suivantes utilisent l'Assistant Installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations sur l’installation du complément, consultez [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).<br /><br /> 1) Exécutez l’installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 2) Dans la page **Rôle d’installation**, sélectionnez **Installation de fonctionnalités SQL Server**.<br /><br /> 3) Dans la page **Sélection de fonctionnalités**, sélectionnez **Complément Reporting Services pour les produits SharePoint**.<br /><br /> 4) Cliquez sur **Suivant** dans les diverses pages suivantes pour compléter les options d’installation.<br /><br/>Pour plus d’informations sur l’installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Installer le premier serveur de rapports en mode SharePoint](http://msdn.microsoft.com/fr-fr/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538).|  
|Vérifiez que le nouveau serveur est opérationnel.|1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système**.<br /><br /> 2) Vérifiez que le nouveau serveur est dans la liste.|  
|Mettez à jour votre solution d'équilibrage de la charge réseau.|Si nécessaire, mettez à jour votre environnement matériel ou logiciel d'équilibrage de la charge réseau pour inclure le nouveau serveur.|  
  
## Voir aussi  
[Ajouter un serveur SharePoint à une batterie de serveurs dans SharePoint Server 2016](https://technet.microsoft.com/library/cc261752(v=office.16).aspx)  
[Ajouter un serveur SharePoint à une batterie de serveurs dans SharePoint Server 2013](https://technet.microsoft.com/library/cc261752(v=office.15).aspx)
  
  