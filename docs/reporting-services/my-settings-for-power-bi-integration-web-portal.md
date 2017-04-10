---
title: "Mes param&#232;tres pour l’int&#233;gration de Power BI (portail web) | Microsoft Docs"
ms.date: "05/18/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pbi"
  - "power bi"
  - "power bi integration"
ms.assetid: 85c2fac7-80bf-45b7-8654-764b5f5231f5
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 15
---
# Mes param&#232;tres pour l’int&#233;gration de Power BI (portail web)
  Grâce à la page **Mes paramètres** du [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], les utilisateurs individuels peuvent gérer leur connexion à [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Lorsque vous parcourez les étapes permettant d’épingler un élément de rapport, vous serez automatiquement invité à vous connecter.  Toutefois, vous pouvez utiliser la page **Mes paramètres** pour vous connecter manuellement ou vous déconnecter.  Si l’option de menu **Mes paramètres** n’est pas visible, cela signifie que le serveur de rapports n’est pas intégré dans  [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Pour plus d’informations, consultez [Intégration du serveur de rapports Power BI &#40;Gestionnaire de configuration&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
## Pourquoi se connecter ?  
 Lorsque vous vous connectez, vous établissez une relation entre votre compte d’utilisateur [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et votre compte [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  La connexion crée un jeton de sécurité, qui est valable pendant 90 jours. Si le jeton expire et que des éléments sont épinglés à Power BI, une notification apparaît.  
   
 ![ssRS_WebPortal_PowerBI_Notification](../reporting-services/media/ssrs-webportal-powerbi-notification.png)    
   
Pour que les vignettes des tableaux de bord [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] soient actualisées, vous devez vous reconnecter via **Mes paramètres**.  
  
![ssRS_WebPortal_PowerBI_SignIn_Again](../reporting-services/media/ssrs-webportal-powerbi-signin-again.png)  
  
Une fois que vous êtes connecté, un jeton de sécurité est créé.  La mise à jour des vignettes de votre tableau de bord se lance sur leurs calendriers configurés précédemment.  
  
## Voir aussi  
 [Intégration du serveur de rapports Power BI &#40;Gestionnaire de configuration&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
 [Épingler des éléments Reporting Services aux tableaux de bord Power BI](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)   
 [Tableaux de bord dans Power BI](https://support.powerbi.com/knowledgebase/articles/424868-dashboards-in-power-bi)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
