---
title: "Utiliser mes abonnements (serveur de rapports en mode natif) | Microsoft Docs"
ms.custom: ""
ms.date: "07/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "abonnements [Reporting Services], page Mes abonnements"
  - "page Mes abonnements [Reporting Services]"
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
caps.latest.revision: 40
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 38
---
# Utiliser mes abonnements (serveur de rapports en mode natif)
Le portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]comprend une page **Mes abonnements** qui centralise tous les abonnements. Vous pouvez utiliser la page *Mes abonnements*pour afficher, modifier, activer, désactiver et supprimer des abonnements existants. En revanche, vous ne pouvez pas l'utiliser pour créer des abonnements.  La page Mes abonnements contient uniquement les abonnements que vous créez. Elle ne répertorie ni les abonnements pilotés par les données ni les abonnements appartenant à d'autres utilisateurs, même si vous figurez parmi les abonnés.
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif|  
  
Le champ de recherche filtre dynamiquement la liste des abonnements. Vous ne pouvez pas rechercher directement les abonnements par nom, pas plus que vous ne pouvez rechercher un abonnement par informations de déclencheur, informations d’état, etc. Pour plus d’informations, consultez [Créer et gérer des abonnements pour les serveurs de rapports en mode natif](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md).
  
## Pour ouvrir la page Mes abonnements  
1. Ouvrez l portail web [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)].
2. Cliquez sur Paramètres ![ssrs_portal_settings_gear](../../reporting-services/subscriptions/media/ssrs-portal-settings-gear.png) dans la barre d’outils.
3. Cliquez sur **Mes abonnements**.

Pour plus d’informations, consultez le [portail web Reporting Services](../../reporting-services/web-portal-ssrs-native-mode.md).

## Utiliser Windows PowerShell pour répertorier les abonnements MySubscriptions  
 ![Contenu relatif à PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.png "Contenu relatif à PowerShell")  
  
 Le script PowerShell suivant renvoie la liste des abonnements et des propriétés d'abonnement pour l'utilisateur actuel. Pour plus d'informations, consultez [Méthode ReportingService2010.ListMySubscriptions](http://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions

```  
  
## Voir aussi  
 [Abonnements pilotés par les données](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [old_Créer et gérer des abonnements pour les serveurs de rapports en mode natif](http://msdn.microsoft.com/fr-fr/7f46cbdb-5102-4941-bca2-5e0ff9012c6b)  
  
  