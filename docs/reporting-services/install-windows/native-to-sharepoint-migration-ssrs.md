---
title: Native pour la Migration de SharePoint (SSRS) | Documents Microsoft
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5b15bec-6fde-4174-bcde-d043307244dd
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 1a58f3884e041b06f741a40ada0bbff6ce7e3181
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

---
# <a name="native-to-sharepoint-migration-ssrs"></a>Migration du mode natif au mode SharePoint (SSRS)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Vous ne pouvez pas effectuer de mise à niveau ou de conversion d'un mode serveur de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers un autre. Par exemple, vous ne pouvez pas mettre à niveau ou convertir un serveur de rapports en mode natif vers le mode SharePoint. Vous ne pouvez pas copier les bases de données du serveur de rapports d'un mode à l'autre car elles utilisent des schémas de base de données différents. Vous pouvez migrer le contenu d'un serveur de rapports à l'autre. Les outils que vous utilisez dépendent du type de mode de serveur de rapports configuré pour les serveurs source et de destination.  
  
##  <a name="bkmk_native_to_sharepoint"></a> Outil de migration Reporting Services  
 L'outil prend en charge la migration du contenu d'un déploiement en mode natif vers un déploiement en mode SharePoint. Il ne prend pas en charge la migration du mode SharePoint vers le mode SharePoint ou du mode SharePoint vers le mode natif.  
  
 Pour plus d’informations, consultez [Outil de migration Reporting Services](http://www.microsoft.com/download/details.aspx?id=29560) (http://www.microsoft.com/download/details.aspx?id=29560).  
  
## <a name="use-script-to-migrate-content"></a>Utiliser un script pour migrer le contenu  
 Si l'outil de migration ne répond pas à vos besoins, vous pouvez migrer manuellement les données du serveur de rapports. Voici un résumé des étapes à effectuer pour la migration des éléments de rapport d'un déploiement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à l'autre. L'approche prend en charge le mode natif ou SharePoint en tant que serveur source ou de destination.  
  
1.  Sauvegardez et restaurez les clés de chiffrement. Il s'agit de la clé utilisée pour chiffrer les données. La clé de chiffrement permet également de chiffrer des mots de passe tels que les mots de passe stockés pour les connexions à la source de données. Toutefois, les mots de passe ne peuvent pas être migrés et vous devrez les taper à nouveau dans l'environnement de destination.  
  
2.  **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Scripts RSS :** écrivez un script Visual Basic qui appelle des méthodes SOAP du service Web Report Server pour copier des données entre des bases de données. Utilisez l'utilitaire **RS.exe** pour exécuter le script. Rs.exe est installé avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    -   [Exemple de script Reporting Services rs.exe pour copier du contenu entre des serveurs de rapports](../../reporting-services/tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md). Les rubriques expliquent comment utiliser l'exemple de script que vous pouvez télécharger sur CodePlex.  
  
    -   Exemple de script rss sur CodePlex, [Script RS.exe de Reporting Services qui migre le contenu d'un serveur de rapports vers un autre](http://azuresql.codeplex.com/releases/view/115207).  
  
    -   [Scripts et PowerShell avec Reporting Services](../../reporting-services/tools/scripting-and-powershell-with-reporting-services.md)  
  
 Le tableau suivant résume les objets [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous pouvez migrer avec des scripts :  
  
|Objet|Peut faire l'objet d'un script|Commentaires|  
|------------|---------------------|--------------|  
|Rapports|Oui|Après la migration, pour entrer à nouveau les mots de passe pour les sources de données.|  
|Sources de données|Oui|Après la migration, reconnectez les rapports aux sources de données.|  
|Modèles|Oui||  
|Datasets|Oui||  
|Parties de rapports||Après la migration, vérifiez ou mettez à jour le chemin d'accès aux parties de rapports.|  
|Planifications|Oui|Consultez la méthode ListSchedules [Subscription and Delivery Methods](../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md).|  
|Abonnements|oui|Reportez-vous à la méthode de la liste des abonnements [méthodes d’abonnement et remise](../../reporting-services/report-server-web-service/methods/subscription-and-delivery-methods.md) et <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A> (méthode).|  
|Instantanés|||

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
