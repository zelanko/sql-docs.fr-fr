---
title: Fonctionnalités de Collection de sites de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: eb321258a8dc87a499479d66ced85b95ce643b6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294119"
---
# <a name="reporting-services-site-collection-features"></a>Fonctionnalités de collection de sites de Reporting Services
  Le mode SharePoint de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit trois fonctionnalités de collection de sites SharePoint. Les fonctionnalités prennent en charge le général [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] mode SharePoint reporting d’environnement, [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], une fonctionnalité de la [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] complément pour [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition et les opérations de gestion pour [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans Administration centrale de SharePoint.  
  
## <a name="site-collection-features"></a>Fonctionnalités de la collection de sites  
 Le tableau ci-dessous décrit les fonctionnalités de la collection de sites [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|**Fonctionnalité Administration centrale du serveur de rapports**|Active les fonctionnalités de gestion de l'intégration avec un serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Cette fonctionnalité est uniquement installée et utilisée dans la collection de sites Administration centrale de SharePoint.<br /><br /> La fonctionnalité d’intégration Report server est automatiquement activée dans la collection de sites Administration centrale de SharePoint après avoir installé le [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] complément pour les produits SharePoint. Dans certaines circonstances, vous devrez activer la fonctionnalité manuellement. Pour activer la fonctionnalité de serveur de rapports, utilisez les pages [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] de la page Paramètres du site de l'Administration centrale de SharePoint.<br /><br /> Le [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] version et versions ultérieures du complément pour SharePoint produits activent la fonctionnalité d’intégration report server pour toutes les collections de sites existantes lorsque le complément est installé. En outre, la fonctionnalité sera automatiquement active pour les nouvelles collections de sites.|  
|**Fonctionnalité d'intégration du serveur de rapports**|Permet la création de rapports détaillés à l’aide de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Cette fonctionnalité est activée par défaut.|  
|**Fonctionnalité d'intégration de Power View**|Active l'exploration interactive de données et la présentation visuelle dans les classeurs PowerPivot et les bases de données tabulaires Analysis Services.<br /><br /> Cette fonctionnalité est accessible via les menus contextuels des sources de données suivantes :<br /><br /> .rdlx<br /><br /> .rsds<br /><br /> fichier de connexion .bism<br /><br /> <br /><br /> Si [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] n'apparaît pas dans les menus contextuels, vérifiez que **Fonctionnalité d'intégration de Power View** est activé.<br /><br /> Cette fonctionnalité est désactivée par défaut.|  
  
## <a name="see-also"></a>Voir aussi  
 [Activer le serveur de rapports et Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Reporting Services paramètres du Site et les fonctions du Site&#40;Mode SharePoint&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
