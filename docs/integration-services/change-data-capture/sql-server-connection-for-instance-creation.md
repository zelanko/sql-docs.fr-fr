---
title: SQL Server Connection for Instance Creation | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 65f20b235b6a3c4bd22ce754467f36a9b03fdaab
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="sql-server-connection-for-instance-creation"></a>Connexion SQL Server pour la création d'une instance
  Une des premières étapes de la création d'une instance Oracle CDC est la création d'une base de données CDC sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible. Cette base de données CDC est activée pour SQL Server CDC et cette activation requiert une connexion membre du rôle serveur fixe `sysadmin` .  
  
 Quand un utilisateur qui démarre l’Assistant **Création d’une instance Oracle CDC** n’est pas membre du rôle serveur fixe `sysadmin` , la boîte de dialogue **Connexion à SQL Server** s’ouvre et vous invite à entrer les informations d’identification pour un membre du rôle `sysadmin` de façon à effectuer la tâche Activer la base de données pour SQL Server CDC. Lorsque la base de données CDC est créée, la connexion `sysadmin` est ignorée et la tâche reprend avec la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'origine utilisée lorsque la console du concepteur Oracle a été ouverte.  
  
## <a name="task-list"></a>Liste des tâches  
 Dans la boîte de dialogue **Connexion à SQL Server** , entrez les informations suivantes :  
  
 **Nom de serveur**  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Authentification**  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**  
  
-   **Authentification SQL Server**: Si vous sélectionnez cette option, vous devez taper **l’identifiant** et le **mot de passe** de l’utilisateur dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
 La connexion doit avoir un rôle de base de données qui permet l'accès à la base de données MSXCDCDB. Il est recommandé que la connexion ait également accès à toutes les bases de données supplémentaires qui sont utilisées, sinon l'utilisateur ne pourra pas afficher les données de ces bases de données.  
  
 **Options**  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion**: Tapez le délai (en secondes) pendant lequel le service de capture de données modifiées pour Oracle attend une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant expiration. La valeur par défaut est **15**.  
  
-   **Délai d’exécution**: Tapez le délai (en secondes) pendant lequel le service Windows de capture de données modifiées Oracle attend l’exécution d’une commande avant expiration. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: sélectionnez **Chiffrer la connexion** pour la communication entre le service de capture de données modifiées Oracle et l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible à l'aide d'une connexion chiffrée.  
  
-   **Avancé**: Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
     Pour plus d’informations sur la boîte de dialogue Propriétés avancées de connexion, consultez [Propriétés avancées de connexion](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer la base de données SQL Server modifiée](../../integration-services/change-data-capture/create-the-sql-server-change-database.md)   
 [Connexion SQL Server des autorisations requises pour le Concepteur de capture de données modifiées](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
