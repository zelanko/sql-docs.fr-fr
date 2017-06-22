---
title: "Activer la fonctionnalité de synchronisation de fichiers de serveur rapport dans l’autorité de certification SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 9
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d9f1b75bc40693248526282a6565db340930601b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-ca"></a>Activer la fonctionnalité de synchronisation de fichiers de serveur rapport dans l’autorité de certification SharePoint
  La fonctionnalité Synchronisation de fichiers de serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise des gestionnaires d'événements SharePoint pour synchroniser le catalogue du serveur de rapports avec les éléments des bibliothèques de documents. Cette fonctionnalité est particulièrement intéressante lorsque des utilisateurs téléchargent fréquemment des éléments de rapport publiés directement dans des bibliothèques de documents SharePoint. Si la fonctionnalité de synchronisation de fichiers n'est pas activée, le contenu est toujours synchronisé mais pas aussi fréquemment.  
  
 La fonctionnalité Synchronisation de fichiers peut être activée dans l’administration des sites SharePoint après installation du complément [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] pour les produits SharePoint.  
  
 Cette fonctionnalité peut être activée et désactivée manuellement site par site, mais pas au niveau de la collection de sites.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint doit être installé. Si ce n'est pas le cas, la fonctionnalité de synchronisation de fichiers ne sera pas visible dans la liste des fonctionnalités du site.  
  
 Pour vérifier l'installation, consultez la liste des applications installées dans le [!INCLUDE[msCoName](../../includes/msconame-md.md)] Panneau de configuration **** Windows. Si le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé, suivez les instructions fournies dans cette rubrique pour activer la fonctionnalité de synchronisation de fichiers.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>Pour activer ou désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports sur un site  
  
1.  Dans la page principale de votre site, cliquez sur le menu **Actions du site** et sélectionnez **Paramètres du site**.  
  
2.  Dans **Actions du site** , cliquez sur **Gérer les fonctionnalités du site**.  
  
3.  Recherchez **Synchronisation de fichiers de serveur de rapports** dans la liste.  
  
4.  Cliquez sur **Activer**.  
  
> [!NOTE]  
>  Pour désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports, appliquez la même procédure, mais cliquez sur **Désactiver**.  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes liés aux parties de rapports (Générateur de rapports et SSRS)](http://msdn.microsoft.com/en-us/d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
 [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
