---
title: Configurer le portail web pour passer des cookies d’authentification personnalisée | Microsoft Docs
ms.date: 04/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2f3200a17f00efedae3f52be7f3b17df31167765
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "65579429"
---
# <a name="configure-the-web-portal-to-pass-custom-authentication-cookies"></a>Configurer le portail web pour passer des cookies d’authentification personnalisée

Si vous utilisez une extension d’authentification personnalisée, vous devez configurer le portail web pour transmettre des cookies d’authentification personnalisée. Sinon, le portail web transmet uniquement des cookies via des requêtes HTTP spécifiques au serveur de rapports. Si vous souhaitez transmettre des cookies supplémentaires, vous devez modifier le fichier RSReportServer.Config.

## <a name="modifying-the-rsreportserverconfig-file"></a>Modification du fichier RSReportServer.Config

Vous pouvez activer le [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] pour transmettre des cookies supplémentaires via le serveur de rapports en ajoutant un élément \<**PassThroughCookies**> aux paramètres de configuration du portail web dans le fichier RSReportServer.config. La transmission de cookies supplémentaires est utile dans une solution d'authentification unique qui requiert non seulement les cookies d'authentification du serveur de rapports mais également les cookies d'un système d'authentification tiers.

Pour activer la transmission de cookies supplémentaires via des requêtes HTTP quand vous utilisez le portail web, définissez les éléments suivants dans le fichier RSReportServer.config :
  
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
[RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Présentation des extensions de sécurité](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
[Configurer et administrer un serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
D’autres questions ? [Essayez le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
