---
title: Instance utilisateur - Configuration du moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- database engine configuration
- database engine configuration, user instance
ms.assetid: dfc27c1e-0fe2-4221-bed5-f52667ddd3c8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ba05d426f9515793ad3a924e375ff9a6ab9f940f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095880"
---
# <a name="database-engine-configuration---user-instance"></a>Configuration du moteur de base de données – Instance utilisateur
  La page **Instance utilisateur** permet de générer une instance distincte du [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour les utilisateurs sans autorisations d’administrateur, et d’ajouter des utilisateurs dans le rôle d’administrateur.  
  
## <a name="option"></a>Option  
 Activer les instances utilisateur  
 Par défaut, cette option est activée. Pour désactiver la fonction qui active les instances utilisateur, désactivez cette case à cocher.  
  
 L'instance utilisateur, également désignée comme instance enfant ou client, est une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est générée par l'instance parent (l'instance principale exécutée en tant que service, telle que [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) pour le compte d'un utilisateur. L'instance utilisateur s'exécute en tant que processus utilisateur dans le contexte de sécurité de cet utilisateur. L'instance utilisateur est isolée de l'instance parent et de toutes les autres instances utilisateur exécutées sur l'ordinateur. La fonction d’instance utilisateur est également appelée RANU (« Run As Normal User », exécution en mode utilisateur normal).  
  
> [!NOTE]  
>  Les connexions configurées en tant que membres du rôle serveur fixe **sysadmin** durant l’installation sont configurées en tant qu’administrateurs dans l’exemple de base de données. Si elles ne sont pas supprimées, elles sont membres du rôle serveur fixe **sysadmin** sur l’instance utilisateur.  
  
 Ajouter l'utilisateur au rôle Administrateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Par défaut, cette option est désactivée. Pour ajouter l'utilisateur du programme d'installation en cours au rôle Administrateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , activez la case à cocher.  
  
 Les utilisateurs [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] qui sont membres de BUILTIN\Administrateurs ne sont pas ajoutés automatiquement au rôle de serveur fixe sysadmin quand ils se connectent à [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Seuls les utilisateurs [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] qui ont été ajoutés explicitement à un rôle d'administrateur de niveau serveur peuvent administrer [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Tous les membres du groupe Built-In\Users peuvent se connecter à l'instance de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , mais ils auront des autorisations limitées pour effectuer les tâches de base de données. Pour cette raison, les utilisateurs dont les privilèges [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] sont hérités de BUILTIN\Administrators et de Built-In\Users dans les versions précédentes de Windows doivent bénéficier explicitement des privilèges d’administrateur dans les instances de [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] qui s’exécutent sur [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)].  
  
 Pour apporter des modifications quelconques aux rôles d'utilisateur une fois le programme d'installation terminé, utilisez l'outil Configuration de la surface d'exposition [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (SQLSAC.exe). Pour mettre à jour la liste des utilisateurs dans le rôle Administrateur système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur le lien **Ajouter un nouvel administrateur** .  
  
 Vérifiez que le champ **Utilisateur à mettre en service** contient les paramètres DomainName\UserName de l’utilisateur dont les autorisations doivent être mises à jour. Sélectionnez le rôle à mettre à jour dans la liste des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le volet **Privilèges disponibles** , puis cliquez sur la flèche droite. Pour ajouter l'utilisateur à tous les rôles disponibles pour toutes les instances disponibles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et tous les rôles disponibles, cliquez sur la double flèche vers la droite.  
  
 Pour implémenter les modifications une fois votre sélection terminée, [!INCLUDE[clickOK](../../includes/clickok-md.md)]. Pour quitter l’outil sans apporter de modification, cliquez sur **Annuler**.  
  
  
