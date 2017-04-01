---
title: "rsAccessedDenied - Erreur Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "erreur rsAccessDenied"
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
caps.latest.revision: 21
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 21
---
# rsAccessedDenied - Erreur Reporting Services
  L’erreur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **rsAccessedDenied** se produit quand un utilisateur n’est pas autorisé à effectuer une action. Par exemple, il ne dispose pas de l'assignation de rôle lui permettant d'ouvrir un rapport ou il n'a pas ouvert son navigateur avec les autorisations requises.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; en mode SharePoint|  
  
-   Si l'erreur s'est produite en accédant au serveur de rapports directement par le biais d'une URL, l'exception est associée à une erreur HTTP 401.  
  
-   Si l'erreur s'est produite lors de l'utilisation du Gestionnaire de rapports ou d'un autre outil, l'erreur apparaît dans une page d'erreurs.  
  
-   Si l'erreur s'est produite pendant une opération planifiée, un abonnement ou une remise, l'erreur apparaît uniquement dans le fichier journal du serveur de rapports.  
  
## Détails  
  
|||  
|-|-|  
|**Nom du produit**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**ID d'événement**|rsAccessedDenied|  
|**Source de l'événement**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**Composant**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**Texte du message**|Les autorisations accordées à l'utilisateur 'mon_domaine\mon_compte' sont insuffisantes pour vous permettre d'accomplir cette opération. (rsAccessDenied) (ReportingServicesLibrary)|  
  
## Action de l'utilisateur  
 L'autorisation d'accéder au contenu et aux opérations d'un serveur de rapports est accordée par l'intermédiaire des attributions de rôles. Dans une nouvelle installation, seuls les administrateurs locaux ont accès à un serveur de rapports. Pour accorder l'accès à d'autres utilisateurs, un administrateur local doit créer une attribution de rôle qui spécifie un utilisateur de domaine ou un compte de groupe, un ou plusieurs rôles définissant les tâches que l'utilisateur peut effectuer, ainsi qu'une étendue (en général, le dossier de base ou le nœud racine de l'arborescence des dossiers du serveur de rapports). Vous pouvez utiliser le Gestionnaire de rapports pour créer les attributions de rôles. Pour plus d'informations, recherchez «Attributions de rôles » dans la documentation en ligne de SQL Server.  
  
 Cette erreur est également due à l'administration locale du serveur de rapports. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## Voir aussi  
 [Attributions de rôles](../../reporting-services/security/role-assignments.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Rôles et autorisations &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md)  
  
  