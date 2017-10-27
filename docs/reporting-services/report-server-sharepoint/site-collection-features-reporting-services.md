---
title: "Fonctionnalités de Reporting Services site collection | Documents Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 7c86f9ecdbbf4955ba224e40c245fc412742fc30
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="reporting-services-site-collection-features"></a>Fonctionnalités de Reporting Services site collection

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)])

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Reporting Services en mode SharePoint fournit trois fonctionnalités de collection de sites SharePoint. Les fonctionnalités prennent en charge le mode SharePoint de Reporting Services général, environnement, de création de rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], une fonctionnalité du SQL Server 2016 Reporting Services Add-in et opérations de gestion de Reporting Services dans l’Administration centrale de SharePoint.

> [!NOTE]
> Intégration de Reporting Services avec SharePoint n’est plus disponible après SQL Server 2016.
  
## <a name="site-collection-features"></a>Fonctionnalités de collection de sites

 Le tableau suivant décrit les fonctionnalités de collection de site de Reporting Services.  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|**Fonctionnalité Administration centrale du serveur de rapports**|Active les fonctionnalités de gestion de l’intégration avec un serveur de rapports Reporting Services. Cette fonctionnalité est uniquement installée et utilisée dans la collection de sites Administration centrale de SharePoint.<br /><br /> La fonctionnalité d’intégration du serveur de rapports est activée automatiquement dans la collection de sites Administration centrale de SharePoint après l’installation du complément [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] pour les produits SharePoint. Dans certaines situations, vous devez activer manuellement la fonctionnalité. Pour activer la fonctionnalité de serveur de rapports, utilisez les pages de Reporting Services dans la page des paramètres du Site de l’Administration centrale SharePoint.<br /><br /> Le [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version de Reporting Services et version ultérieure du complément pour SharePoint produits activer la fonctionnalité d’intégration de report server pour toutes les collections de sites existantes lorsque le complément est installé. En outre, la fonctionnalité est automatiquement active pour les nouvelles collections de sites.|  
|**Fonctionnalité d'intégration du serveur de rapports**|Permet la création de rapports détaillés à l’aide de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Reporting Services<br /><br /> Cette fonctionnalité est activée par défaut.|  
|**Fonctionnalité d'intégration de Power View**|Active l’exploration interactive de données et la présentation visuelle dans les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et les bases de données tabulaires Analysis Services.<br /><br /> Cette fonctionnalité est accessible via les menus contextuels des sources de données suivantes :<br /><br /> **.rdlx**<br /><br /> **.rsds**<br /><br /> fichier de connexion**.bism** <br /><br /> <br /><br /> Si [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] n'apparaît pas dans les menus contextuels, vérifiez que **Fonctionnalité d'intégration de Power View** est activé.<br /><br /> Cette fonctionnalité est désactivée par défaut.|  

## <a name="next-steps"></a>Étapes suivantes

[Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
[Paramètres et fonctions du site Reporting Services &#40;mode SharePoint&#41;](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)   
[Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

