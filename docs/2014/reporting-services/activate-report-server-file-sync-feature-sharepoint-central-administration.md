---
title: Activer la fonctionnalité de synchronisation fichiers Report Server dans l’Administration centrale de SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 83ffe3e16bad4fdc1c60a818dd7f07bd47e00cb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153656"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>Activer la fonctionnalité Synchronisation de fichiers de serveur de rapports dans l'Administration centrale de SharePoint
  La fonctionnalité Synchronisation de fichiers de serveur de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] utilise des gestionnaires d'événements SharePoint pour synchroniser le catalogue du serveur de rapports avec les éléments des bibliothèques de documents. Cette fonctionnalité est particulièrement intéressante lorsque des utilisateurs téléchargent fréquemment des éléments de rapport publiés directement dans des bibliothèques de documents SharePoint. Si la fonctionnalité de synchronisation de fichiers n'est pas activée, le contenu est toujours synchronisé mais pas aussi fréquemment.  
  
 La fonctionnalité de synchronisation de fichiers peut être activée dans l’Administration des sites SharePoint après avoir installé le [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] complément pour les produits SharePoint.  
  
 Cette fonctionnalité peut être activée et désactivée manuellement site par site, mais pas au niveau de la collection de sites.  
  
## <a name="prerequisites"></a>Prérequis  
 Le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour SharePoint doit être installé. Si ce n'est pas le cas, la fonctionnalité de synchronisation de fichiers ne sera pas visible dans la liste des fonctionnalités du site.  
  
 Pour vérifier l'installation, consultez la liste des applications installées dans le [!INCLUDE[msCoName](../includes/msconame-md.md)] **Panneau de configuration** Windows. Si le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] complément est installé, suivez les instructions de cette rubrique pour activer la fonctionnalité de synchronisation de fichiers report server.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>Pour activer ou désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports sur un site  
  
1.  Dans la page principale de votre site, cliquez sur le menu **Actions du site** et sélectionnez **Paramètres du site**.  
  
2.  Dans **Actions du site** , cliquez sur **Gérer les fonctionnalités du site**.  
  
3.  Recherchez **Synchronisation de fichiers de serveur de rapports** dans la liste.  
  
4.  Cliquez sur **Activer**.  
  
> [!NOTE]  
>  Pour désactiver la fonctionnalité Synchronisation de fichiers de serveur de rapports, appliquez la même procédure, mais cliquez sur **Désactiver**.  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes de parties de rapport &#40;rapport Générateur et SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [Activer le serveur de rapports et les fonctionnalités d’intégration Power View dans SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  