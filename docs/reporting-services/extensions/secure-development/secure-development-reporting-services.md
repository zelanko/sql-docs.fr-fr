---
title: "Développement sécurisé (Reporting Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: cb8a4502531dbe3ee23434ea126457196b56c701
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="secure-development-reporting-services"></a>Développement sécurisé (Reporting Services)
  Le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fournit un système de sécurité fiable qui peut exécuter du code dans des contextes de sécurité soumis à des contraintes définies par l’administrateur. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] utilise le système de sécurité du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], appelé sécurité d'accès du code (ou sécurité basée sur les preuves). Sous la sécurité d'accès du code, un utilisateur doit être approuvé pour pouvoir accéder à une ressource, mais si le code qu'il exécute n'est pas approuvé, l'accès à la ressource lui est refusé.  
  
 La sécurité basée sur le code, par opposition à celle basée sur des utilisateurs spécifiques, permet de spécifier la sécurité pour les assemblys personnalisés ou les extensions de données, de remise, de rendu et de sécurité que vous développez pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Votre code d'extension peut être exécuté par un nombre illimité d'utilisateurs de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], tous inconnus au moment du développement. Les assemblys personnalisés ou extensions que vous développez nécessitent des stratégies de sécurité spécifiques dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Ces stratégies de sécurité sont représentées en tant que types dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Pour plus d'informations sur la sécurité d'accès du code, consultez la rubrique « Sécurité d'accès du code » dans la documentation du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sécurité d’accès du code dans Reporting Services](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)  
 Présente la configuration des stratégies et de la sécurité d'accès du code pour les extensions et assemblys personnalisés dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Présentation des stratégies de sécurité](../../../reporting-services/extensions/secure-development/understanding-security-policies.md)  
 Décrit les différents types d'assemblys dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et explique comment la sécurité d'accès du code affecte les autorisations de code.  
  
 [À l’aide de Reporting Services Security Policy Files](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)  
 Décrit les différents composants [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et les fichiers de configuration de stratégies correspondants.  
  
  
