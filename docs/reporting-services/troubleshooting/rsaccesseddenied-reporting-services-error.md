---
title: rsAccessedDenied - Erreur Reporting Services | Microsoft Docs
ms.date: 05/22/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0063256e371585fe6d63a1a635aa286fca5a7d39
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "66270228"
---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied - erreur Reporting Services
  L’erreur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**rsAccessedDenied** se produit quand un utilisateur n’est pas autorisé à effectuer une action. Par exemple, il ne dispose pas de l'attribution de rôle lui permettant d'ouvrir un rapport ou il n'a pas ouvert son navigateur avec les autorisations requises.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; en mode SharePoint|  
  
- Si l'erreur s'est produite en accédant au serveur de rapports directement par le biais d'une URL, l'exception est associée à une erreur HTTP 401.  
  
- Si l’erreur s’est produite lors de l’aide du portail web, l’exception est généralement mappée à une erreur HTTP 401 ou autres définies par la page d’erreur HTML.  
  
- Si l'erreur s'est produite pendant une opération planifiée, un abonnement ou une remise, l'erreur apparaît uniquement dans le fichier journal du serveur de rapports.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|**Nom du produit**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**ID d'événement**|rsAccessedDenied|  
|**Source de l'événement**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**Composant**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**Texte du message**|Les autorisations accordées à l'utilisateur 'mon_domaine\mon_compte' sont insuffisantes pour vous permettre d'accomplir cette opération. (rsAccessDenied) (ReportingServicesLibrary)|  
  
## <a name="user-action"></a>Action requise  
 L'autorisation d'accéder au contenu et aux opérations d'un serveur de rapports est accordée par l'intermédiaire des attributions de rôles. Dans une nouvelle installation, seuls les administrateurs locaux ont accès à un serveur de rapports. Pour accorder l'accès à d'autres utilisateurs, un administrateur local doit créer une attribution de rôle qui spécifie un utilisateur de domaine ou un compte de groupe, un ou plusieurs rôles définissant les tâches que l'utilisateur peut effectuer, ainsi qu'une étendue (en général, le dossier de base ou le nœud racine de l'arborescence des dossiers du serveur de rapports). Vous pouvez utiliser le portail web pour créer des attributions de rôle. Pour plus d’informations, consultez [Attributions de rôle](../../reporting-services/security/role-assignments.md).  
  
 Cette erreur est également due à l'administration locale du serveur de rapports. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributions de rôles](../../reporting-services/security/role-assignments.md)  
 [Octroi d'autorisations sur un serveur de rapports en mode natif](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
 [Rôles et autorisations &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md)  
  