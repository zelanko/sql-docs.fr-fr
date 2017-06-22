---
title: "Configurer le portail Web pour passer des Cookies d’authentification personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 0f1131c191fa64c6dc6f2a074a9cd5db7a8b0e1b
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="configure-the-web-portal-to-pass-custom-authentication-cookies"></a>Configurer le portail web pour passer des cookies d’authentification personnalisée

Si vous utilisez une extension d’authentification personnalisée, vous devez configurer le portail web pour transmettre des cookies d’authentification personnalisé. Dans le cas contraire, le portail web transmet uniquement les cookies via des requêtes HTTP spécifiques au serveur de rapports. Si vous souhaitez transmettre des cookies supplémentaires, vous devez modifier le fichier RSReportServer.Config.

## <a name="modifying-the-rsreportserverconfig-file"></a>Modification du fichier RSReportServer.Config

Vous pouvez activer la [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] pour transmettre des cookies supplémentaires via le serveur de rapports en ajoutant un \< **PassThroughCookies**> élément pour les paramètres de configuration du portail web dans le fichier RSReportServer.config. La transmission de cookies supplémentaires est utile dans une solution d'authentification unique qui requiert non seulement les cookies d'authentification du serveur de rapports mais également les cookies d'un système d'authentification tiers.

Pour activer les cookies supplémentaires à transmettre via des requêtes HTTP lors de l’utilisation du portail web, définissez les éléments suivants dans le fichier RSReportServer.config :
  
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
  
## <a name="see-also"></a>Voir aussi

[Authentification avec le serveur de rapports](../../reporting-services/security/authentication-with-the-report-server.md)   
[Fichier de configuration RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Vue d’ensemble des Extensions de sécurité](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
[Configurer et administrer un serveur de rapports &#40; En Mode natif de SSRS &#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
D’autres questions ? [Essayez le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
