---
title: Activer la fonctionnalité de synchronisation de fichiers de serveur rapport dans l’Administration centrale de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 69d059807b7d48fe71cffb120c73fa9aa004a8bb
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018001"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint
  La fonctionnalité Synchronisation de fichiers de serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] utilise des gestionnaires d'événements SharePoint pour synchroniser le catalogue du serveur de rapports avec les éléments des bibliothèques de documents. Cette fonctionnalité est particulièrement intéressante lorsque des utilisateurs téléchargent fréquemment des éléments de rapport publiés directement dans des bibliothèques de documents SharePoint. Si la fonctionnalité de synchronisation de fichiers n'est pas activée, le contenu est toujours synchronisé mais pas aussi fréquemment.  
  
 La fonctionnalité Synchronisation de fichiers peut être activée dans l’administration des sites SharePoint après installation du complément [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] pour les produits SharePoint.  
  
 Cette fonctionnalité peut être activée et désactivée manuellement site par site, mais pas au niveau de la collection de sites.  
  
## <a name="prerequisites"></a>Prérequis  
 Le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour SharePoint doit être installé. Si ce n'est pas le cas, la fonctionnalité de synchronisation de fichiers ne sera pas visible dans la liste des fonctionnalités du site.  
  
 Pour vérifier l'installation, consultez la liste des applications installées dans le [!INCLUDE[msCoName](../includes/msconame-md.md)] **Panneau de configuration** Windows. Si le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est installé, suivez les instructions fournies dans cette rubrique pour activer la fonctionnalité de synchronisation de fichiers.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>Pour activer ou désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports sur un site  
  
1.  Dans la page principale de votre site, cliquez sur le menu **Actions du site** et sélectionnez **Paramètres du site**.  
  
2.  Dans **Actions du site** , cliquez sur **Gérer les fonctionnalités du site**.  
  
3.  Recherchez **Synchronisation de fichiers de serveur de rapports** dans la liste.  
  
4.  Cliquez sur **Activer**.  
  
> [!NOTE]  
>  Pour désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports, appliquez la même procédure, mais cliquez sur **Désactiver**.  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes de parties de rapports &#40;Générateur de rapports et SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
