---
title: Modifier les informations d’identification Assistant (SSRS en Mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.changecredentialswizard.F1
helpviewer_keywords:
- Change Credentials Wizard
- report server database, reconfigure
ms.assetid: 9eb4060a-9c3e-41e0-8767-3cfaebc45de7
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0163bff016043e31bf36a689220976b85e4ae097
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244291"
---
# <a name="change-credentials-wizard-ssrs-native-mode"></a>Assistant Modification des informations d'identification (SSRS en mode natif)
  Le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit l'Assistant Modification des informations d'identification pour vous guider à travers les étapes de reconfiguration du compte que le serveur de rapports utilise pour se connecter à la base de données du serveur de rapports. Lorsque vous modifiez les informations d'identification, le Gestionnaire de configuration met à jour toutes les autorisations et informations de connexion de base de données sur le serveur de base de données pour la base de données du serveur de rapports en cours d'utilisation par le serveur de rapports.  
  
 Pour démarrer l’Assistant, cliquez sur **modifier les références** sur la page de base de données dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Pour obtenir des instructions sur la façon de démarrer le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, consultez [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
## <a name="options"></a>Options  
 **Serveur de base de données**  
 Spécifie le nom de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance qui exécute la base de données de serveur de rapports.  
  
 Pour vous connecter à la [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance, vous devez utiliser les informations d’identification qui ont l’autorisation de se connecter au serveur et mise à jour les informations de base de données. Le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager utilise vos informations d’identification Windows actuelles, mais si vous n’avez pas de connexion ou la base de données d’autorisations, vous pouvez spécifier une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion de base de données.  
  
 Vous ne pouvez pas spécifier d'autres informations d'identification Windows. Si vous souhaitez vous connecter en tant qu’un autre utilisateur de Windows, connectez-vous en tant que cet utilisateur, puis démarrez le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager.  
  
 **Informations d’identification**  
 Spécifie le compte utilisé par le serveur de rapports pour se connecter à la base de données du serveur de rapports. Les valeurs valides incluent le compte de service du service Web Report Server, un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion de base de données définie sur le [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance que vous utilisez pour héberger le serveur de rapports, ou un compte Windows. Si vous utilisez un compte Windows, vous pouvez spécifier un compte local (*\<nom_ordinateur >\\< nom d’utilisateur\>*) si le serveur de rapports et de la base de données se trouvent sur le même ordinateur ou un utilisateur de domaine compte (*\<domaine >\\< nom d’utilisateur\>*) s’ils sont sur des ordinateurs différents dans le même domaine.  
  
 Le serveur de rapports crée alors une connexion de base de données et attribue les autorisations de base de données au compte que vous spécifiez.  
  
 Le serveur de rapports ne crée pas le compte lui-même. Le compte que vous spécifiez doit déjà exister et doit être valide pour votre configuration de déploiement. Plus particulièrement, si la base de données se trouve sur un ordinateur distant et que vous souhaitez utiliser un compte Windows, vous devez spécifier un compte qui a les autorisations de connexion sur cet ordinateur.  
  
 Si l’ordinateur est dans un domaine différent ou non approuvé, envisagez d’utiliser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion de base de données. Pour plus d’informations sur le choix d’un compte, consultez [configurer une connexion de base de données de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
 **Résumé**  
 Vérifiez les paramètres avant l'Assistant ne s'exécute.  
  
 **État d’avancement et fin**  
 Surveillez la progression de chaque tâche.  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/database-ssrs-native-mode.md)   
 [Modifier la base de données Assistant &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Configurer une connexion de base de données de serveur de rapports &#40;Gestionnaire de Configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)  
  
  
