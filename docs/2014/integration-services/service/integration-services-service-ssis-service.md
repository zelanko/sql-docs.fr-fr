---
title: Service Integration Services (Service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, about Integration Services service
- SQL Server Integration Services service
- service [Integration Services],about Integration Services service
- service [Integration Services]
- SQL Server Integration Services, service
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7eb8f74e271b9d5c19cedab4fd25069eb5a0e2b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62766686"
---
# <a name="integration-services-service-ssis-service"></a>Service Integration Services (Service SSIS)
  Les rubriques de cette section décrivent le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], un service Windows de gestion des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Ce service n'est pas obligatoire pour créer, enregistrer et exécuter des packages Integration Services. 
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] prend en charge le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 À compter [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , stocke des objets, des paramètres et des `SSISDB` données opérationnelles dans la base de données pour [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] les projets que vous avez déployés sur le serveur à l’aide du modèle de déploiement de projet. Le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , qui est une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , héberge la base de données. Pour plus d’informations sur la base de données, consultez [Catalogue SSIS](../catalog/ssis-catalog.md). Pour plus d’informations sur le déploiement de projets sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Déployer des projets sur le serveur Integration Services](../deploy-projects-to-integration-services-server.md).  
  
## <a name="management-capabilities"></a>Fonctionnalités de gestion  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est un service Windows pour la gestion des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'est disponible que dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
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
  
## <a name="startup-type-for-integration-services-service"></a>Type de démarrage du service Integration Services  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est installé quand vous installez le composant [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est démarré et le type de démarrage du service est défini comme étant automatique. Le service doit être en cours d'exécution pour surveiller les packages stockés dans le magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Le magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] peut aussi bien être la base de données msdb dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que les dossiers désignés dans le système de fichiers.  
  
 Le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n’est pas nécessaire si vous souhaitez seulement concevoir et exécuter des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Cependant, le service est nécessaire pour répertorier et surveiller les packages à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [définir les propriétés du service Integration Services](../set-the-properties-of-the-integration-services-service.md)  
  
-   [afficher les événements du service Integration Services](../view-events-for-the-integration-services-service.md)  
  
  
