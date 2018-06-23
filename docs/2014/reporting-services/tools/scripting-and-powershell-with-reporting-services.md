---
title: Scripts et PowerShell avec Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 0d76693f37506cd78a7d198520344cb55f9d142f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051861"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Scripts et PowerShell avec Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] prend en charge un large éventail de scénarios de développement et de gestion via script, notamment l’utilitaire de ligne de commande rs.exe, les applets de commande PowerShell pour les serveurs de rapports en mode SharePoint et en exploitant la [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] modèle objet à partir de PowerShell pour l’installation Native et Mode SharePoint.  
  
-   Les administrateurs peuvent écrire les scripts en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] pour automatiser le déploiement et la gestion d'une installation du serveur de rapports. Les administrateurs peuvent également générer et exécuter des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] qui créent, configurent et mettent à jour une base de données du serveur de rapports. Les administrateurs peuvent aussi utiliser les fonctionnalités d'enregistrement et de lecture de scripts de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] pour automatiser les tâches régulières de maintenance.  
  
-   Les développeurs peuvent créer des applications personnalisées incluant des scripts. Vous pouvez exécuter des scripts qui effectuent des appels au service Web Report Server. Pratiquement chaque opération que vous pouvez écrire en code managé peut également l'être écrite sous forme de script.  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] prend en charge [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] script .NET comme langage de script pouvant être traités par l’utilitaire RS.exe, un hôte de script qui s’exécute sur le serveur de rapports.  
  
## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Exemples et applets de commande PowerShell du mode SharePoint de Reporting Services  
 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell")  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Le mode SharePoint inclut [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] applets de commande pour l’administration de serveur de rapports.  
  
-   La section[PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) inclut les exemples suivants :  
  
    -   Créer une application de service et un proxy  
  
    -   Analyse et mise à jour d'une extension de remise  
  
    -   Obtenir et définir les propriétés de la base de données d'application Reporting Services, par exemple le délai d'expiration de la base de données  
  
    -   Extensions de données Liste  
  
## <a name="reporting-services-object-model-and-powershell-samples"></a>Exemples du modèle d'objet Reporting Services et de Powershell  
 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell")  
  
 Appel du modèle d'objet principal par PowerShell, valide en grande partie pour les modes natif et SharePoint, comme les tâches de migration et d'abonnement, et d'autres exemples associés de tâches d'abonnement dans SQL15.  
  
-   [Utiliser PowerShell pour modifier et répertorier Reporting Services Subscription Owners and Run a Subscription](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
-   [Utilisation de PowerShell pour créer une machine virtuelle Azure avec un serveur de rapports en mode natif](http://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   Consultez la section « Accéder aux classes WMI à l'aide de PowerShell » dans [Accéder au fournisseur WMI de Reporting Services](access-the-reporting-services-wmi-provider.md).  
  
-   [Comment administrer SSRS à l'aide de PowerShell](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell).scriptin  
  
## <a name="rsexe-scripting-samples"></a>Exemples de scripts RS.exe  
  
-   [Exemple Script Reporting Services rs.exe pour migrer le contenu entre les serveurs de rapports](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Pour obtenir des exemples supplémentaires de script, d'application et d'extension, consultez les [exemples de produit SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md)   
 [Écrire des scripts pour les tâches d'administration et de déploiement](script-deployment-and-administrative-tasks.md)   
 [Écrire des scripts avec l'utilitaire rs.exe et le service Web](script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  