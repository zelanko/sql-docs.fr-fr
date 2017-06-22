---
title: "Configurer des stratégies de contrôle d’intégrité (utilitaire SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d1e3fdfceb5d12bb37e9f8289b03e5e3db3e84ad
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="configure-health-policies-sql-server-utility"></a>Configurer des stratégies de contrôle d'intégrité (utilitaire SQL Server)
  Utilisez le tableau de bord de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour consulter les paramètres des ressources de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les applications de la couche Données. Pour plus d’informations, consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Pour consulter les résultats d'une stratégie de contrôle d'intégrité de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , connectez-vous à un point de contrôle de l'utilitaire de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [Utiliser l’Explorateur de l’utilitaire pour gérer l’Utilitaire SQL Server](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les stratégies de contrôle d’intégrité de l’utilitaire peuvent être configurées pour des applications de la couche Données et des instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les stratégies d’intégrité peuvent être définies globalement pour toutes les applications de la couche Données et toutes les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Elles peuvent également être définies individuellement pour chaque application de la couche Données et pour chaque instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="monitoring-policies-for-data-tier-applications"></a>Stratégies de surveillance pour les applications de couche Données  
 Les stratégies de surexploitation et de sous-exploitation pour les applications de la couche Données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivantes :  
  
-   utilisation du processeur par l'application de couche Données ;  
  
-   espace de fichier de l'application de couche Données pour les fichiers de base de données ;  
  
-   espace de fichier de l'application de couche Données pour les volumes de stockage ;  
  
-   utilisation du processeur de l'ordinateur.  
  
> [!NOTE]  
>  Le volume de stockage et l'utilisation du processeur sont des stratégies en lecture seule pour les applications de la couche Données.  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance globales pour les applications de la couche Données, consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d).  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance pour des applications de la couche Données spécifiques, consultez [Détails des applications de la couche Données déployées &#40;utilitaire SQL Server&#41;](http://msdn.microsoft.com/library/79c41dd9-abcb-434e-9326-00a341d5c867).  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a>Stratégies de surveillance pour les instances gérées de SQL Server  
 Les stratégies de surexploitation et de sous-exploitation pour les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont les suivantes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les fichiers de base de données ;  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les volumes de stockage ;  
  
-   utilisation du processeur de l'ordinateur.  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance globales pour les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d).  
  
 Pour plus d’informations sur l’affichage ou la modification des stratégies de surveillance globales pour des instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiques, consultez [Détails de l’instance gérée &#40;utilitaire SQL Server&#41;](http://msdn.microsoft.com/library/6e51b7bb-a733-4852-8c33-7f4dbdf931c2).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;utilitaire SQL Server&#41;](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
