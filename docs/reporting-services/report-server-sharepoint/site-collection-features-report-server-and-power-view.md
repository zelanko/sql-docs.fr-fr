---
title: "Activer le serveur de rapports et les fonctionnalités d’intégration Power View dans SharePoint | Documents Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: e97378914a59fab938fc3e4c7926847effcffc94
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>Activer le serveur de rapports et les fonctionnalités d’intégration Power View dans SharePoint

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)])

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Les fonctionnalités de collection de site de Reporting Services sont activées par défaut après avoir installé le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] complément pour les produits SharePoint. Dans certaines situations, vous devez activer manuellement les fonctionnalités.  

> [!NOTE]
> Intégration de Reporting Services avec SharePoint n’est plus disponible après SQL Server 2016.

 Si vous installez le complément Reporting Services pour les produits SharePoint 2010 après l’installation du produit SharePoint, puis la fonctionnalité d’intégration de serveur de rapports et la fonctionnalité d’intégration Power View sont uniquement activées pour les collections de sites racine. Pour les autres collections de sites, vous devez activer manuellement les fonctionnalités. Par exemple, si vous avez une collection de sites **http://[my nom du serveur] /sites/ [nom de collection de site]** vous devez activer manuellement les fonctionnalités de collection de site de Reporting Services.  
  
 Lorsqu’il n’existe aucune collection de sites racine, le complément Reporting Services consignera un message semblable au suivant.  
  
 « L'application Web SharePoint 80 n'a pas de collection de sites racine »  
  
 Le message se trouve dans le journal d’installation du complément, nommé « RS_SP_ # .log » où # est un numéro à incrémentation. Le fichier journal se trouve dans le dossier Temp les utilisateurs en cours, par exemple C:\Users\\[nom utilisateur] \AppData\Local\Temp. Pour plus d’informations sur les options de journalisation du complément, consultez [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  

## <a name="activate-the-report-server-and-power-view-integration-site-collection-features"></a>Activer les fonctionnalités de collection de site intégration Report Server et Power View
  
1.  Ouvrez votre navigateur sur le site où vous souhaitez les fonctionnalités de Reporting Services active.  
  
2.  Cliquez sur **Actions du site**.  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Cliquez sur **Fonctionnalités de la collection de sites** dans le groupe Administration de la collection de sites.  
  
5.  Recherchez **Fonctionnalité d'intégration Report Server** ou **Fonctionnalité d'intégration de Power View** dans la liste.  
  
6.  Cliquez sur **Activer**.  
  
 Pour désactiver les fonctionnalités, vous pouvez utiliser la même procédure en cliquant sur **Désactiver** au lieu d' **Activer**.  
  
## <a name="activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a>Activer ou la fonctionnalité de collection de site administration centrale de désactiver les Services de création de rapports
  
1.  Ouvrez votre navigateur dans l'Administration centrale de SharePoint.  
  
2.  Cliquez sur **Actions du site**.  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Cliquez sur **Fonctionnalités de la collection de sites** dans le groupe Administration de la collection de sites.  
  
5.  Recherchez **Fonctionnalité d'administration centrale du serveur de rapports** dans la liste.  
  
6.  Cliquez sur **Activer**.  
  
 Pour désactiver la fonctionnalité, vous pouvez utiliser la même procédure en cliquant sur **Désactiver** au lieu d' **Activer**.  
  
## <a name="next-steps"></a>Étapes suivantes

Une fois la fonctionnalité activée, vous pouvez continuer l'intégration de serveur.

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
