---
title: Attributions de rôles | Microsoft Docs
ms.date: 05/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- users [Reporting Services]
- roles [Reporting Services]
- role-based security [Reporting Services], role assignments
- groups [Reporting Services]
- security [Reporting Services], role assignments
ms.assetid: 600e112c-1897-48a6-93c0-6e9f3f12dc01
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a6fe3c0cd82d8ee8b92948d76d4f7cdb5fa4cf73
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65570566"
---
# <a name="role-assignments"></a>Attributions de rôles

Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les *attributions de rôles* déterminent l’accès aux éléments stockés et au serveur de rapports proprement dit. Une attribution de rôle est composée des parties suivantes :  
  
- Un élément sécurisable dont vous souhaitez contrôler l'accès. Dossiers, rapports et ressources sont des exemples d'éléments sécurisables.  
  
- Un utilisateur ou un groupe pouvant être authentifié par la sécurité Windows ou un autre mécanisme d'authentification.  
  
- Les définitions de rôles définissent un ensemble de tâches autorisées et incluent :
  - **Navigateur**
  - **Gestionnaire de contenu**
  - **Mes rapports**
  - **Serveur de publication**
  - **Générateur de rapports**
  - **Administrateur système**
  - **Utilisateur système**

 Les attributions de rôles sont héritées au sein de l’arborescence des dossiers, et sont automatiquement héritées par les éléments contenus suivants :

- **Rapports**
- **Sources de données partagées**
- **Ressources**
- **Sous-dossiers**

Vous pouvez passer outre la sécurité héritée en définissant les attributions de rôles des éléments individuels. Toutes les parties de la hiérarchie de dossiers doivent être sécurisées par au moins une attribution de rôle. Vous ne pouvez pas créer d’élément non sécurisé ou manipuler des paramètres d’une manière qui produise un élément non sécurisé.  
  
 La diagramme suivant illustre une attribution de rôle qui mappe un groupe et un utilisateur spécifique au rôle **Serveur de publication** du dossier B.  
  
 ![Diagramme des attributions de rôles](../../reporting-services/security/media/report-securityarch.gif "Diagramme des attributions de rôles")  
Diagramme des attributions de rôles  
  
## <a name="system-level-and-item-level-role-assignments"></a>Attributions de rôles de niveau système et de niveau élément

 Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , la sécurité basée sur les rôles s'articule autour des niveaux suivants :

- Les attributions de rôles au niveau élément contrôlent l’accès aux éléments dans la hiérarchie des dossiers du serveur de rapports, tels que :
  - rapports
  - Dossiers
  - Modèles de rapport
  - sources de données partagées
  - Autres ressources

- Les attributions de rôles au niveau élément sont définies quand vous créez une attribution de rôle sur un élément spécifique ou sur le dossier racine.

- Les attributions de rôles système autorisent les opérations qui ont pour étendue l’ensemble du serveur. Par exemple, la capacité à gérer des travaux est une opération au niveau du système. Une attribution de rôle système n’est pas l’équivalent d’un administrateur système. Elle ne confère pas d’autorisations avancées qui accordent le contrôle total d’un serveur de rapports.

Une attribution de rôle système ne permet pas d’accéder aux éléments de la hiérarchie des dossiers. La sécurité système et la sécurité de niveau élément s'excluent mutuellement. Parfois, vous pouvez être amené à créer une attribution de rôle au niveau système et une attribution de rôle au niveau élément afin d’accorder un accès suffisant à un utilisateur ou à un groupe.

## <a name="users-and-groups-in-role-assignments"></a>Utilisateurs et groupes dans les attributions de rôles

 Les utilisateurs ou les comptes de groupe que vous spécifiez dans les attributions de rôles sont des comptes de domaine. Le serveur de rapports fait référence à des utilisateurs et des groupes d’un domaine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows (ou un autre modèle de sécurité si vous utilisez une extension de sécurité personnalisée), mais ne crée ni ne gère ces utilisateurs et groupes.

De toutes les attributions de rôles qui s'appliquent à un élément donné, deux attributions ne peuvent pas spécifier le même utilisateur ou groupe. Si un compte d'utilisateur est également membre d'un compte de groupe, et que vous avez des attributions de rôles pour les deux, vous pouvez disposer de l'ensemble combiné des tâches des deux attributions de rôles.

Quand vous ajoutez un utilisateur à un groupe qui fait déjà partie d’une attribution de rôle, vous devez réinitialiser Internet Information Services (IIS) afin que la nouvelle attribution de rôle prenne effet.

## <a name="predefined-role-assignments"></a>Attributions de rôles prédéfinies

 Par défaut, les attributions de rôles prédéfinies intégrées permettent aux administrateurs locaux de gérer le serveur de rapports. Vous pouvez ajouter des attributions de rôles pour accorder l’accès à d’autres utilisateurs.

 Pour plus d'informations sur les attributions de rôles prédéfinies qui assurent la sécurité par défaut, consultez [Rôles prédéfinis](../../reporting-services/security/role-definitions-predefined-roles.md).  

## <a name="see-also"></a>Voir aussi

 [Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md)

 [Modifier ou supprimer une attribution de rôle &#40; portail web SSRS&#41;](../../reporting-services/security/role-assignments-modify-or-delete.md)

 [Définir les autorisations sur les éléments du serveur de rapports sur un site SharePoint &#40;Reporting Services en mode intégré SharePoint&#41;](../../reporting-services/security/set-permissions-for-report-server-items-on-a-sharepoint-site.md)

 [Octroi d'autorisations sur un serveur de rapports en mode natif](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
