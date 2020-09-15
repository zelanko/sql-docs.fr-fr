---
description: Accorder des autorisations sur un serveur de rapports en mode natif
title: Accorder des autorisations sur un serveur de rapports en mode natif | Microsoft Docs
ms.date: 05/14/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 82fba1144cdb970d97b8aac4938fd7c3e8fe0980
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88373295"
---
# <a name="grant-permissions-on-a-native-mode-report-server"></a>Accorder des autorisations sur un serveur de rapports en mode natif
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise l'autorisation basée sur les rôles et un sous-système d'authentification pour déterminer qui est habilité à effectuer des opérations et à accéder aux éléments d'un serveur de rapports. L'autorisation basée sur les rôles catégorise en rôles l'ensemble des actions qu'un utilisateur ou groupe peut effectuer. L'authentification repose sur l'authentification Windows intégrée ou sur un module d'authentification personnalisé que vous fournissez. Vous pouvez utiliser des rôles prédéfinis ou personnalisés avec chacun de ces types d'authentifications.
  
## <a name="use-roles-to-grant-report-server-access"></a>Utiliser des rôles pour accorder l’accès au serveur de rapports
 Tous les utilisateurs interagissent avec un serveur de rapports dans le contexte d'un rôle qui définit un niveau spécifique d'accès. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclut des rôles prédéfinis que vous pouvez affecter aux utilisateurs et aux groupes pour fournir l’accès immédiat à un serveur de rapports. **Gestionnaire de contenu**, **Éditeur** et **Lecteur** sont des exemples de rôles prédéfinis. Chaque rôle définit un ensemble de tâches associées. Par exemple, un **serveur de publication** est autorisé à ajouter des rapports et à créer des dossiers pour stocker ces mêmes rapports.
  
 Les attributions de rôles sont généralement héritées d'un nœud parent, mais vous pouvez rompre l'héritage d'autorisation en créant une attribution de rôles pour un élément particulier. Un utilisateur membre du rôle **Gestionnaire de contenu** pour un rapport peut être membre du rôle **Lecteur** pour un autre rapport.
  
 Pour accorder l’accès aux éléments et opérations du serveur de rapports :
  
1. Examinez les rôles prédéfinis pour déterminer si vous pouvez les utiliser en l'état. Si vous devez ajuster les tâches ou définir des rôles supplémentaires, effectuez ces tâches avant de commencer à assigner des utilisateurs à des rôles spécifiques. Pour plus d’informations sur chaque rôle, consultez [Rôles prédéfinis](../../reporting-services/security/role-definitions-predefined-roles.md).
  
1. Identifiez les utilisateurs et les groupes qui doivent accéder au serveur de rapports, et à quel niveau. Vous devez attribuer le rôle **Lecteur** ou le rôle **Générateur de rapports** à la plupart des utilisateurs. Le rôle **Éditeur** doit être attribué à un nombre restreint d’utilisateurs. Attribuez le rôle **Gestionnaire de contenu** uniquement à quelques utilisateurs.
  
1. Utilisez le portail web pour attribuer des rôles à chaque utilisateur ou groupe qui a besoin d’accéder au dossier de base. Le dossier de base est le dossier situé tout en haut de l’arborescence des dossiers du serveur de rapports.
  
1. Au niveau du site, dans la page **Paramètres du site** du portail web, créez une attribution de rôles au niveau système pour chaque utilisateur et groupe en utilisant les rôles prédéfinis **Utilisateur système** et **Administrateur système**.
  
1. Créez autant d'attributions de rôles supplémentaires que nécessaire pour des dossiers, des rapports et d'autres éléments spécifiques. Évitez de créer un grand nombre d'attributions de rôles. Si vous en créez trop, il sera difficile de gérer les différents niveaux d’autorisations pour chaque utilisateur.
  
> [!NOTE]  
>  Si vous avez configuré un serveur de rapports de telle sorte qu'il s'exécute en mode intégré SharePoint, vous devez définir des autorisations sur le site SharePoint de manière à accorder l'accès aux éléments du serveur de rapports. Pour plus d’informations, consultez [Accord d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).
> 
> L’intégration de Reporting Services à SharePoint n’est plus disponible après SQL Server 2016.
  
## <a name="who-sets-permissions"></a>Qui définit les autorisations ?
 Initialement, seuls les utilisateurs qui sont membres du groupe des administrateurs locaux peuvent accéder au serveur de rapports. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est installé avec deux attributions de rôles par défaut qui accordent un accès au niveau élément et au niveau système aux membres du groupe des administrateurs locaux. Les administrateurs locaux peuvent utiliser ces attributions de rôles intégrées pour accorder l’accès au serveur de rapports à d’autres utilisateurs et gérer les éléments du serveur de rapports. Les attributions de rôles intégrées ne peuvent pas être supprimées. Un administrateur local a toujours l'autorisation de gérer entièrement une instance de serveur de rapports.
 
 Une configuration supplémentaire est requise avant que vous puissiez administrer une instance du serveur de rapports sur un ordinateur local qui exécute Windows Vista ou Windows Server 2008. Pour plus d’informations, consultez [Configurer un serveur de rapports en mode natif pour l’administration locale &#40;SSRS&#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).
  
## <a name="how-permissions-are-stored"></a>Stockage des autorisations
 Les attributions et les définitions de rôles sont stockées dans la base de données du serveur de rapports. Si vous utilisez de nombreux outils clients ou interfaces de programmation, tout accès est soumis aux autorisations définies pour l’instance du serveur de rapports dans son ensemble. Si vous configurez plusieurs serveurs de rapports au sein d’un déploiement de type scale-out, les attributions de rôles que vous définissez sur une instance sont stockées dans une base de données partagée et sont utilisées par toutes les autres instances du même déploiement scale-out. Dans la mesure où les attributions de rôles sont stockées avec les éléments qu'elles sécurisent, vous pouvez déplacer la base de données vers une autre instance du serveur de rapports sans perdre les autorisations définies.
  
## <a name="tasks-and-tools-for-managing-permissions"></a>Tâches et outils de gestion des autorisations
 Utilisez les outils suivants pour gérer les définitions et les attributions de rôles.
  
|Outil|Tâches|  
|----------|-----------|  
|Management Studio : Permet de voir, modifier, créer et supprimer des définitions de rôles|[Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)|  
|Portail web : Permet d’attribuer des rôles à des utilisateurs et à des groupes|[Octroyer un accès utilisateur à un serveur de rapports](../../reporting-services/security/grant-user-access-to-a-report-server.md)<br /><br /> [Modifier ou supprimer une attribution de rôle](../../reporting-services/security/role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a>Voir aussi
 - [Rôles prédéfinis](../../reporting-services/security/role-definitions-predefined-roles.md)  
 - [Accord d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 - [Authentification auprès du serveur de rapports](../../reporting-services/security/authentication-with-the-report-server.md)  
 - [Créer et gérer des attributions de rôle](../../reporting-services/security/create-and-manage-role-assignments.md)  
 - [Sécurité et protection Reporting Services](../../reporting-services/security/reporting-services-security-and-protection.md)  
 - [Gestion du contenu du serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)  
  
  
