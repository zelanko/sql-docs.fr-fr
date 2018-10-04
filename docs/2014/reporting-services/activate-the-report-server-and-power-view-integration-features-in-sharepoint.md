---
title: Activer le serveur de rapports et Power View Integration Features in SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1ab486390e8da36d14d5aac1e1049a5836dd2be9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081825"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Activer les fonctionnalités d'intégration Report Server et Power View dans SharePoint
  Les fonctionnalités de collection de sites de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sont généralement activées par défaut après l’installation du complément [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] pour les produits SharePoint. Dans certaines circonstances, vous devrez activer les fonctionnalités manuellement.  
  
 Si vous installez le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint 2010 après l'installation du produit SharePoint, la fonctionnalité d'intégration du serveur de rapports et la fonctionnalité d'intégration de vue de remplissage sont uniquement activées pour les collections de sites racine. Pour les autres collections de sites, vous devez activer manuellement les fonctionnalités. Par exemple, si vous avez une collection de sites **http://[my nom du serveur] /sites/ [nom de collection de sites]** vous devez activer manuellement le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] les fonctionnalités de collection de sites.  
  
 Lorsqu’il n’existe aucune collection de sites racine, le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] complément journalise un message semblable au suivant.  
  
 « L'application Web SharePoint 80 n'a pas de collection de sites racine »  
  
 Le message se trouve dans le journal d'installation du complément, nommé « RS_SP_#.log » où # est un nombre incrémenté. Le fichier journal se trouve dans le dossier Temp de l’utilisateur actuel, par exemple C:\Users\\[nom utilisateur]\AppData\Local\Temp. Pour plus d’informations sur les options de journalisation avec le complément, consultez [installer ou désinstaller le logiciel complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Dans cette rubrique :  
  
-   [Pour activer les fonctionnalités d'intégration de collections de sites Report Server et Power View :](#bkmk_features)  
  
-   [Pour activer ou désactiver la fonctionnalité de collection de sites dans l'Administration centrale de Reporting Services :](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> Pour activer les fonctionnalités d'intégration de collections de sites Report Server et Power View :  
  
1.  Ouvrez votre navigateur sur le site où vous souhaitez activer les fonctionnalités de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
2.  Cliquez sur **Actions du site**.  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Cliquez sur **Fonctionnalités de la collection de sites** dans le groupe Administration de la collection de sites.  
  
5.  Recherchez **Fonctionnalité d'intégration Report Server** ou **Fonctionnalité d'intégration de Power View** dans la liste.  
  
6.  Cliquez sur **Activer**.  
  
 Pour désactiver les fonctionnalités, vous pouvez utiliser la même procédure en cliquant sur **Désactiver** au lieu d' **Activer**.  
  
##  <a name="bkmk_centraladmin"></a> Pour activer ou désactiver la fonctionnalité de collection de sites dans l'Administration centrale de Reporting Services :  
  
1.  Ouvrez votre navigateur dans l'Administration centrale de SharePoint.  
  
2.  Cliquez sur **Actions du site**.  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Cliquez sur **Fonctionnalités de la collection de sites** dans le groupe Administration de la collection de sites.  
  
5.  Recherchez **Fonctionnalité d'administration centrale du serveur de rapports** dans la liste.  
  
6.  Cliquez sur **Activer**.  
  
 Pour désactiver la fonctionnalité, vous pouvez utiliser la même procédure en cliquant sur **Désactiver** au lieu d' **Activer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois la fonctionnalité activée, vous pouvez continuer l'intégration de serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer ou désinstaller le complément Services Reporting pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
