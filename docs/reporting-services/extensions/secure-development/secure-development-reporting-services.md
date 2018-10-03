---
title: Développement sécurisé (Reporting Services) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 024c3d3fdfb0f756376491e8b85503ffc13d149e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47800947"
---
# <a name="secure-development-reporting-services"></a>Développement sécurisé (Reporting Services)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] constitue un système de sécurité fiable qui peut exécuter du code dans des contextes de sécurité soumis à de fortes contraintes et définis par l’administrateur. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] utilise le système de sécurité du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], appelé sécurité d'accès du code (ou sécurité basée sur les preuves). Sous la sécurité d'accès du code, un utilisateur doit être approuvé pour pouvoir accéder à une ressource, mais si le code qu'il exécute n'est pas approuvé, l'accès à la ressource lui est refusé.  
  
 La sécurité basée sur le code, par opposition à celle basée sur des utilisateurs spécifiques, permet de spécifier la sécurité pour les assemblys personnalisés ou les extensions de données, de remise, de rendu et de sécurité que vous développez pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Votre code d'extension peut être exécuté par un nombre illimité d'utilisateurs de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], tous inconnus au moment du développement. Les assemblys personnalisés ou extensions que vous développez nécessitent des stratégies de sécurité spécifiques dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Ces stratégies de sécurité sont représentées en tant que types dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Pour plus d'informations sur la sécurité d'accès du code, consultez la rubrique « Sécurité d'accès du code » dans la documentation du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 [Sécurité d'accès du code dans Reporting Services](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)  
 Présente la configuration des stratégies et de la sécurité d'accès du code pour les extensions et assemblys personnalisés dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Présentation des stratégies de sécurité](../../../reporting-services/extensions/secure-development/understanding-security-policies.md)  
 Décrit les différents types d'assemblys dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et explique comment la sécurité d'accès du code affecte les autorisations de code.  
  
 [Utilisation des fichiers de stratégie de sécurité Reporting Services](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)  
 Décrit les différents composants [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] et les fichiers de configuration de stratégies correspondants.  
  
  
