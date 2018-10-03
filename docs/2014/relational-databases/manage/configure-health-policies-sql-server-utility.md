---
title: Configurer des stratégies de contrôle d’intégrité (utilitaire SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: da394108767b6d6583bbf185bcc1c3a699051ed6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062861"
---
# <a name="configure-health-policies-sql-server-utility"></a>Configurer des stratégies de contrôle d'intégrité (utilitaire SQL Server)
  Utilisez le tableau de bord de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour consulter les paramètres des ressources de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les applications de la couche Données. Pour plus d’informations, consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](sql-server-utility-features-and-tasks.md).  
  
 Pour consulter les résultats d'une stratégie de contrôle d'intégrité de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , connectez-vous à un point de contrôle de l'utilitaire de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [Utiliser l’Explorateur de l’utilitaire pour gérer l’Utilitaire SQL Server](use-utility-explorer-to-manage-the-sql-server-utility.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les stratégies de contrôle d’intégrité de l’utilitaire peuvent être configurées pour des applications de la couche Données et des instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les stratégies d’intégrité peuvent être définies globalement pour toutes les applications de la couche Données et toutes les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Elles peuvent également être définies individuellement pour chaque application de la couche Données et pour chaque instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="monitoring-policies-for-data-tier-applications"></a>Stratégies de surveillance pour les applications de couche Données  
 Les stratégies de surexploitation et de sous-exploitation pour les applications de la couche Données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivantes :  
  
-   utilisation du processeur par l'application de couche Données ;  
  
-   espace de fichier de l'application de couche Données pour les fichiers de base de données ;  
  
-   espace de fichier de l'application de couche Données pour les volumes de stockage ;  
  
-   utilisation du processeur de l'ordinateur.  
  
> [!NOTE]  
>  Le volume de stockage et l'utilisation du processeur sont des stratégies en lecture seule pour les applications de la couche Données.  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance globales pour les applications de la couche Données, consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](../../database-engine/utility-administration-sql-server-utility.md).  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance pour des applications de la couche Données spécifiques, consultez [Détails des applications de la couche Données déployées &#40;utilitaire SQL Server&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a>Stratégies de surveillance pour les instances gérées de SQL Server  
 Les stratégies de surexploitation et de sous-exploitation pour les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivantes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les fichiers de base de données ;  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les volumes de stockage ;  
  
-   utilisation du processeur de l'ordinateur.  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance globales pour les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](../../database-engine/utility-administration-sql-server-utility.md).  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance globales pour des instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiques, consultez [Détails de l’instance gérée &#40;utilitaire SQL Server&#41;](../../database-engine/managed-instance-details-sql-server-utility.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l’utilitaire SQL Server](sql-server-utility-features-and-tasks.md)   
 [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;utilitaire SQL Server&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
