---
title: Ajouter un serveur web frontal Reporting Services supplémentaire à une batterie de serveurs | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: d7a11bda-ae26-49ac-b071-37d83cae5afe
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7996ea2541963d0c7a2060d819667e25d102305
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108960"
---
# <a name="add-an-additional-reporting-services-web-front-end-to-a-farm"></a>Ajouter un serveur Web frontal Reporting Services supplémentaire à une batterie
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Le mode SharePoint inclut les composants nécessaires pour les serveurs d’applications et les serveurs web frontaux. Cette rubrique traite de l'installation des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requis pour un serveur Web frontal, y compris les pages d'application utilisées par les fonctionnalités [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] telles que les abonnements, les alertes de données et [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. L'installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] principale nécessaire pour un serveur Web frontal consiste à installer le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint 2010.  
  
## <a name="prerequisites"></a>Conditions préalables requises  
  
-   Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.  
  
-   L'ordinateur doit être attaché à un domaine.  
  
-   Vous devez connaître le nom du serveur de base de données existant qui héberge la configuration et les bases de données de contenu SharePoint.  
  
-   Le serveur de base de données doit être configuré pour autoriser les connexions de base de données distantes.  S'il ne l'est pas, vous ne pourrez pas joindre le nouveau serveur à la batterie car il ne pourra pas établir de connexion aux bases de données de configuration SharePoint.  
  
-   Le nouveau serveur devra avoir la même version de SharePoint installée que celle exécutée par les serveurs de batterie actuels. Par exemple, si SharePoint 2010 Service Pack 1 (SP1) est déjà installé sur la batterie, vous devrez installer également le SP1 sur le nouveau serveur pour qu'il puisse rejoindre la batterie.  
  
-   Consultez les rubriques supplémentaires suivantes pour comprendre les exigences du système et des versions :  
  
     [Instructions d'utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
## <a name="steps"></a>Étapes  
 Les étapes de cette rubrique partent du principe qu'un administrateur de batterie de serveurs SharePoint installe et configure le serveur. Le diagramme illustre un environnement à trois niveaux classique et les éléments numérotés sont décrits dans la liste suivante :  
  
-   (1) Plusieurs serveurs Web frontaux. Les serveurs Web frontaux ont besoin du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint 2010. Les étapes suivantes ajoutent un deuxième serveur d'applications à cette couche.  
  
-   (2) Deux serveurs d'applications exécutant [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et des sites Web, par exemple Administration centrale.  
  
-   (3) Deux serveurs de base de données SQL Server.  
  
-   (4) Représente une solution d'équilibrage de la charge réseau matérielle ou logicielle  
  
 ![Ajouter SSRS à un nouveau WFE SharePoint](../../../2014/sql-server/install/media/rs-sharepointscale-wfe.gif "Ajouter SSRS à un nouveau WFE SharePoint")  
  
 Les étapes suivantes impliquent qu'un administrateur procède à l'installation et à la configuration du serveur.  
  
|Étape|Description et lien|  
|----------|--------------------------|  
|Exécutez l'Outil de préparation des produits SharePoint 2010.|Vous devez disposer du support d'installation pour SharePoint 2010. L’outil de préparation est **PrerequisiteInstaller. exe** sur le support d’installation.|  
|Installez un produit SharePoint 2010.|1) sélectionnez le type d’installation de la **batterie de serveurs** .<br /><br /> 2) sélectionnez **terminé** pour le type de serveur.<br /><br /> 3) Lorsque l’installation est terminée, n’exécutez pas l’Assistant Configuration des produits SharePoint si SharePoint 2010 SP1 est installé sur votre batterie de serveurs SharePoint existante. Vous devez installer SharePoint SP1 avant d'exécuter l'Assistant Configuration des produits SharePoint.|  
|Installer SharePoint Server 2010 SP1|Si SharePoint 2010 SP1 est installé sur votre batterie de serveurs SharePoint existante, téléchargez et installez SharePoint[https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697)2010 SP1 à partir de :.<br /><br /> Pour plus d'informations sur SharePoint 2010 SP1, consultez [Problèmes connus lors de l'installation d'Office 2010 SP1 et de SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126):|  
|Exécutez l'Assistant Configuration des produits SharePoint pour ajouter le serveur à la batterie.|1) dans le groupe de programmes **produits Microsoft sharepoint 2010** , cliquez sur **Assistant Configuration des produits Microsoft SharePoint 2010**.<br /><br /> 2) dans la page **se connecter à une batterie de serveurs** , sélectionnez **se connecter à une batterie** de serveurs existante, puis cliquez sur **suivant**.<br /><br /> 3) dans la page **spécifier les paramètres de la base de données de configuration** , tapez le nom du serveur de base de données utilisé pour la batterie de serveurs existante et le nom de la base de données de configuration. Cliquez sur **Suivant**.<br />**&#42;&#42;  &#42;&#42;importante** Si un message d’erreur semblable au suivant s’affiche et que vous avez vérifié que vous disposez des autorisations, vérifiez les Protocoles activés pour la configuration réseau SQL Server dans **SQL Server Configuration Manager**. «Échec de la connexion au serveur de base de données. Assurez-vous que la base de données existe, qu’il s’agit d’un serveur SQL Server et que vous disposez des autorisations appropriées pour accéder au serveur.»<br />**&#42;&#42;  &#42;&#42;importante** Si vous voyez l' **État du produit et du correctif**de la batterie de serveurs de pages, vous devez passer en revue les informations de la page et mettre à jour le serveur avec les fichiers nécessaires pour pouvoir continuer à joindre le serveur à la batterie de serveurs.<br /><br /> 4) dans la page **spécifier les paramètres de sécurité** de la batterie, tapez le mot de passe de votre batterie de serveurs, puis cliquez sur **suivant**. Cliquez sur **Suivant** dans la page de confirmation pour exécuter l'Assistant.<br /><br /> 5) cliquez sur **suivant** pour exécuter l' **Assistant Configuration de batterie de serveurs**.|  
|Vérifiez que le serveur a été ajouté à la batterie de serveurs SharePoint.|1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système** .<br /><br /> 2) Vérifiez que le nouveau serveur est ajouté et que l'état est correct.<br /><br /> 3) pour supprimer ce serveur du rôle WFE, cliquez sur **gérer les services sur le serveur** et arrêtez l' **application Web service Microsoft SharePoint Foundation**.|  
|Installez le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément pour les produits SharePoint 2010.|Il existe plusieurs méthodes pour installer le complément. Les étapes suivantes utilisent l'Assistant Installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Pour plus d’informations sur l’installation du complément, consultez [installer ou désinstaller le complément Reporting Services pour sharepoint &#40;sharepoint 2010 et sharepoint 2013&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Exécuter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] l’installation :<br /><br /> 1) Dans la page **Rôle d’installation** , sélectionnez **Installation de fonctionnalités SQL Server**.<br /><br /> 2) dans la page **sélection de fonctionnalités** , sélectionnez **Reporting Services complément pour les produits SharePoint**<br /><br /> 3) cliquez sur **suivant** sur les différentes pages suivantes pour terminer les options d’installation.<br /><br /> Pour en savoir plus sur l’installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez la section [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).|  
|Vérifiez que le nouveau serveur est opérationnel.|1) Dans l’Administration centrale de SharePoint, cliquez sur **Gérer les serveurs de cette batterie** dans le groupe **Paramètres système** .<br /><br /> 2) Vérifiez que le nouveau serveur est dans la liste.|  
|Mettez à jour votre solution d'équilibrage de la charge réseau.|Si nécessaire, mettez à jour votre environnement matériel ou logiciel d'équilibrage de la charge réseau pour inclure le nouveau serveur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter un serveur Web ou d’applications à la batterie de serveurs (SharePoint Server 2010)](https://technet.microsoft.com/library/bb218968.aspx?missingurl=%2fen-us%2flibrary%2fe1aeaddf-6ee4-43a9-82b7-db20b68c71db\(Office.14\))   
 [Configurer les services (SharePoint Server 2010)](https://technet.microsoft.com/library/ee794878.aspx)  
  
  
