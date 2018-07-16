---
title: Sécurité et protection de Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3be671426856e57e62ea7de3733f6109bbcd0a31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232449"
---
# <a name="reporting-services-security-and-protection"></a>Sécurité et protection de Reporting Services
  Utilisez les informations de cette section pour en savoir plus sur les fonctionnalités de sécurité de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Cette section décrit également les modèles d’autorisation et les fournisseurs d’authentification pris en charge dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="extended-protection-for-authentication"></a>Protection étendue de l'authentification  
 À compter de [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], la prise en charge de la protection étendue de l'authentification est disponible. La fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge l'utilisation de la liaison de canal et la liaison de service pour améliorer la protection de l'authentification. Les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent être utilisées avec un système d'exploitation qui prend en charge la protection étendue. Pour plus d’informations, consultez [Protection étendue pour l’authentification avec Reporting Services](extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Authentification et autorisation  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit différents types d’authentification pour que les utilisateurs et les applications clientes puissent être authentifiés par le serveur de rapports. L'utilisation du bon type d'authentification pour votre serveur de rapports permet à votre organisation d'obtenir le niveau de sécurité approprié requis par votre organisation. Pour plus d’informations, consultez [Authentification avec le serveur de rapports](authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise également les rôles et les autorisations pour contrôler l’accès au contenu dans le catalogue du serveur de rapports (en d’autres termes, qui peut accéder à quoi, et comment y accéder). Pour plus d’informations, consultez [Rôles et autorisations &#40;Reporting Services&#41;](roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descriptions de tâche|Liens|  
|-----------------------|-----------|  
|Configurez le SSL (Secure Socket Layer) pour sécuriser les connexions clientes au serveur de rapports.|[Configurer des connexions SSL sur un serveur de rapports en mode natif](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
