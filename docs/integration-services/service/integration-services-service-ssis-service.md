---
title: "Service Integration Services (Service SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service Integration Services, à propos du service Integration Services"
  - "service SQL Server Integration Services"
  - "service [Integration Services], à propos du service Integration Services"
  - "service [Integration Services]"
  - "SQL Server Integration Services, service"
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
caps.latest.revision: 61
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 61
---
# Service Integration Services (Service SSIS)
  Les rubriques de cette section décrivent le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], un service Windows de gestion des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Ce service n'est pas obligatoire pour créer, enregistrer et exécuter des packages Integration Services. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] prend en charge le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stocke des objets, des paramètres et des données opérationnelles dans la base de données **SSISDB** pour les projets que vous avez déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à l’aide du modèle de déploiement de projet. Le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], qui est une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], héberge la base de données. Pour plus d’informations sur la base de données, consultez [Catalogue SSIS](../../integration-services/service/ssis-catalog.md). Pour plus d’informations sur le déploiement de projets sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
## Fonctionnalités de gestion  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est un service Windows pour la gestion des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'est disponible que dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 L’exécution du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] offre les fonctionnalités de gestion suivantes :  
  
-   Démarrage des packages stockés localement et à distance  
  
-   Arrêt des packages exécutés localement et à distance  
  
-   Surveillance des packages exécutés localement et à distance  
  
-   Importation et exportation de packages  
  
-   Gestion du stockage des packages  
  
-   Personnalisation des dossiers de stockage  
  
-   Arrêt des packages exécutés si le service est arrêté  
  
-   Affichage du journal des événements Windows  
  
-   Connexion à plusieurs serveurs [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
## Type de démarrage du service Integration Services  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est installé quand vous installez le composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est démarré et le type de démarrage du service est défini comme étant automatique. Le service doit être en cours d'exécution pour surveiller les packages stockés dans le magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Le magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] peut aussi bien être la base de données msdb dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que les dossiers désignés dans le système de fichiers.  
  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas nécessaire si vous souhaitez seulement concevoir et exécuter des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Cependant, le service est nécessaire pour répertorier et surveiller les packages à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## Tâches associées  
  
-   [définir les propriétés du service Integration Services](../../integration-services/service/set-the-properties-of-the-integration-services-service.md)  
  
-   [afficher les événements du service Integration Services](../../integration-services/service/view-events-for-the-integration-services-service.md)  
  
  