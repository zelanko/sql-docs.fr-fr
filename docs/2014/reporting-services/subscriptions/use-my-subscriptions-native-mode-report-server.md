---
title: Utiliser mes abonnements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 650fe0fe02841c55caf0cfba864eb739386ca48a
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783147"
---
# <a name="use-my-subscriptions"></a>Utiliser Mes abonnements
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Gestionnaire de rapports comprend une page **mes abonnements** qui réorganise tous vos abonnements dans un même emplacement. Vous pouvez utiliser cette page pour afficher, modifier et supprimer des abonnements existants. En revanche, vous ne pouvez pas l'utiliser pour créer des abonnements.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode|  
  
 La page Mes abonnements vous permet de trier les abonnements par dossier, rapport, description, déclencheur, date d'exécution ou état. Toutes les valeurs sont triées par ordre alphabétique, à l'exception de Dernière exécution, qui est trié par ordre chronologique.  
  
 La page Mes abonnements contient uniquement les abonnements que vous créez. Elle ne répertorie ni les abonnements pilotés par les données ni les abonnements appartenant à d'autres utilisateurs, même si vous figurez parmi les abonnés.  
  
 Vous ne pouvez pas rechercher directement les abonnements par nom, pas plus que vous ne pouvez rechercher un abonnement par informations de déclencheur, informations d'état, etc. Pour plus d’informations, consultez [créer, modifier et supprimer des abonnements &#40;standard Reporting Services en&#41;mode natif](create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
## <a name="how-to-use-my-subscriptions"></a>Utilisation de la page Mes abonnements  
 Vous affichez la page Mes abonnements via le Gestionnaire de rapports. Pour ce faire, dans la barre d'outils globale du Gestionnaire de rapports, cliquez sur **Mes abonnements** .  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Utiliser Windows PowerShell pour répertorier les abonnements MySubscriptions  
 ![Contenu relatif à PowerShell](../media/rs-powershellicon.jpg "Contenu relatif à PowerShell")  
  
 Le script PowerShell suivant renvoie la liste des abonnements et des propriétés d'abonnement pour l'utilisateur actuel. Pour plus d'informations, consultez [Méthode ReportingService2010.ListMySubscriptions](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```powershell
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions
```  
  
## <a name="see-also"></a>Voir aussi  
 [Data-Driven Subscriptions](data-driven-subscriptions.md)   
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Créer et gérer des abonnements pour les serveurs de rapports en mode Natif](../create-manage-subscriptions-native-mode-report-servers.md)  
