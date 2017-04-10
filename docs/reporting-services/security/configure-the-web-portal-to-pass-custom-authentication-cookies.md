---
title: "Configurer le Gestionnaire de rapports pour passer des cookies d&#39;authentification personnalis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "authentification [Reporting Services]"
  - "extensions [Reporting Services], sécurité personnalisée"
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# Configurer le Gestionnaire de rapports pour passer des cookies d&#39;authentification personnalis&#233;e
  Si vous utilisez une extension d’authentification personnalisée, vous devez configurer le [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] pour transmettre des cookies d’authentification personnalisée. Sinon, le [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] transmet uniquement des cookies via des demandes HTTP spécifiques au serveur de rapports. Si vous souhaitez transmettre des cookies supplémentaires, vous devez modifier le fichier RSReportServer.Config.  
  
## Modification du fichier RSReportServer.Config  
 Vous pouvez activer le [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] pour transmettre des cookies supplémentaires via le serveur de rapports en ajoutant un élément \<**PassThroughCookies**> aux paramètres de configuration du [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] dans le fichier RSReportServer.config. La transmission de cookies supplémentaires est utile dans une solution d'authentification unique qui requiert non seulement les cookies d'authentification du serveur de rapports mais également les cookies d'un système d'authentification tiers.  
  
 Pour activer la transmission de cookies supplémentaires via des requêtes HTTP lorsque vous utilisez le [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)], définissez les éléments ci-après dans le fichier RSReportServer.config :  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## Voir aussi  
 [Authentification avec le serveur de rapports](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Fichier de configuration RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Présentation des extensions de sécurité](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
 [Configurer et administrer un serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  