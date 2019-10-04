---
title: Reporting Services l’authentification en mode SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ff0a4f38bf9ee7d9c27fbc07308084ed3272f95d
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952099"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>Authentification en mode SharePoint de Reporting Services
  Utilisez la page **Authentification en mode SharePoint de Reporting Services** de l'Assistant Installation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour spécifier les informations d'identification du compte de service utilisé dans l'installation actuelle de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les informations d'identification seront utilisées pour créer un pool d'applications SharePoint. Une application de service SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sera également créée. Le nom de l'application de service contiendra le nom de l'instance précédente de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Options  
  
-   L'option **Nom de compte de pool d'applications SSRS :** est en lecture seule. La valeur est automatiquement remplie avec la valeur actuelle de l'installation existante [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] que vous mettez à niveau.  
  
-   L'option **Mot de passe du compte du pool d'applications SSRS :** sera désactivée si le compte de pool d'applications ne nécessite pas de mot de passe. Par exemple, « NT Authority\NetworkService ». Si le compte de pool d'applications nécessite un mot de passe, vous ne pouvez pas poursuivre la mise à niveau tant que vous ne tapez pas le mot de passe correct.  
  
 Pour plus d’informations, consultez [mettre à niveau et migrer des Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à niveau et migrer Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
