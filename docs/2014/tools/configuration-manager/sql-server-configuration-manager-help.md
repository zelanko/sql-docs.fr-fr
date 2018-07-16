---
title: Aide sur le Gestionnaire de configuration SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, help
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d91b9cebf140bc68e9df55b33eaa092a10a75254
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286461"
---
# <a name="sql-server-configuration-manager-help"></a>Aide sur le Gestionnaire de configuration SQL Server
  Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous permet de configurer les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la connectivité réseau. Pour créer ou gérer des objets de base de données, configurer la sécurité et écrire des requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] , utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d'informations sur [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Cette section contient les rubriques d'aide accessibles au moyen de la touche F1, relatives aux boîtes de dialogue du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le Gestionnaire de configuration ne peut pas configurer les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="services"></a>Services  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère les services liés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bien que beaucoup de ces tâches puissent être réalisées à l'aide de la boîte de dialogue Services [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, il est important de noter que le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des opérations supplémentaires sur les services qu'il gère, telles que l'application des autorisations adéquates lors de la modification du compte des services. L'utilisation de la boîte de dialogue Services Windows normale pour configurer l'un des services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut provoquer un dysfonctionnement de celui-ci.  
  
 Utilisez le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accomplir les tâches suivantes relatives aux services :  
  
-   Démarrer, arrêter et suspendre les services  
  
-   Configurer les services de manière à ce qu'ils démarrent automatiquement ou manuellement, désactiver les services ou modifier d'autres paramètres des services  
  
-   Modifier les mots de passe des comptes utilisés par les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Démarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’indicateurs de trace (paramètres de ligne de commande)  
  
-   Afficher les propriétés des services  
  
## <a name="sql-server-network-configuration"></a>Configuration du réseau SQL Server  
 Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous permet de réaliser les tâches suivantes relatives aux services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installés sur cet ordinateur :  
  
-   Activer ou désactiver un protocole réseau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Configurer un protocole réseau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
> [!NOTE]  
>  Pour vous procurer un didacticiel sommaire sur la manière de configurer les protocoles et de se connecter au [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], consultez [Didacticiel : Mise en route du moteur de base de données](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).  
  
## <a name="sql-server-native-client-configuration"></a>Configuration de SQL Server Native Client  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connectent à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de la bibliothèque réseau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous permet de réaliser les tâches suivantes relatives aux applications clientes installées sur cet ordinateur :  
  
-   Pour les applications clientes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur cet ordinateur, spécifier l'ordre des protocoles lors de la connexion à des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Configurer les protocoles de connexion clients  
  
-   Pour les applications clientes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , créer des alias pour les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]afin que les clients puissent se connecter à l'aide d'une chaîne de connexion personnalisée  
  
 Pour plus d'informations sur chacune de ces tâches, consultez la rubrique d'aide correspondante accessible à l'aide de la touche F1.  
  
#### <a name="to-open-sql-server-configuration-manager"></a>Pour ouvrir le Gestionnaire de configuration SQL Server  
  
-   Dans le menu **Démarrer** , pointez successivement sur **Tous les programmes**, sur **Microsoft SQL Server** (version), sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
## <a name="see-also"></a>Voir aussi  
 [Services SQL Server](../../../2014/tools/configuration-manager/sql-server-services.md)   
 [Configuration du réseau SQL Server](sql-server-network-configuration.md)   
 [Configuration de SQL Native Client 11.0](../../../2014/tools/configuration-manager/sql-native-client-11-0-configuration.md)   
 [Choix d’un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
