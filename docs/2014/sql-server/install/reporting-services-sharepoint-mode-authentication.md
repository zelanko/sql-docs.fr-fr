---
title: L’authentification en Mode SharePoint de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 704d104b8834675f7511c952db7fafb9fcccafd3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247809"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Authentification en mode SharePoint de Reporting Services
  Utilisez la page **Authentification en mode SharePoint de Reporting Services** de l'Assistant Installation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour spécifier les informations d'identification du compte de service utilisé dans l'installation actuelle de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les informations d'identification seront utilisées pour créer un pool d'applications SharePoint. Une application de service SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera également créée. Le nom de l'application de service contiendra le nom de l'instance précédente de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Options  
  
-   L'option **Nom de compte de pool d'applications SSRS :** est en lecture seule. La valeur est automatiquement remplie avec la valeur actuelle de l'installation existante [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous mettez à niveau.  
  
-   L'option **Mot de passe du compte du pool d'applications SSRS :** sera désactivée si le compte de pool d'applications ne nécessite pas de mot de passe. Par exemple, “NT Authority\NetworkSerivce”. Si le compte de pool d'applications nécessite un mot de passe, vous ne pouvez pas poursuivre la mise à niveau tant que vous ne tapez pas le mot de passe correct.  
  
 Pour plus d’informations, consultez [mise à niveau et migrer Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628) (http://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à niveau et migrer Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
