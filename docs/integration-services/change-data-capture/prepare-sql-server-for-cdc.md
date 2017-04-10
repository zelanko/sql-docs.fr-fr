---
title: "Pr&#233;parer SQL Server pour la capture de donn&#233;es modifi&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "prepSqlSrv"
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Pr&#233;parer SQL Server pour la capture de donn&#233;es modifi&#233;es
  Le service de capture de données modifiées Oracle requiert que toutes les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cibles contiennent la base de données MSXDBCDC. Vous créez cette base de données à l'aide de l'action Préparer SQL Server dans la console de configuration du service de capture de données modifiées. Cela crée un script spécial qui est exécuté pour créer les tables requises, les procédures stockées et autres artefacts nécessaires pour cette base de données. Cette tâche est effectuée une seule fois pour chaque instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible.  
  
 Pour plus d'informations sur la base de données MSXDBCDC, consultez Base de données MSXDBCDC.  
  
 Dans la console de configuration du service de capture de données modifiées, cliquez sur **Préparer SQL Server**. Si cette option n’est pas disponible, vérifiez que **Services de capture de données modifiées locaux** est sélectionné dans le volet gauche de la console.  
  
## Options  
  
### Nom de serveur  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### Authentification  
 Sélectionnez l'une des options suivantes :  
  
-   **Authentification Windows**  
  
-   **Authentification SQL Server** : si vous sélectionnez cette option, vous devez taper le **Nom d’utilisateur** et le **Mot de passe** pour l’utilisateur dans l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
 Pour préparer l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la capture de données modifiées Oracle, la connexion doit avoir l'autorisation d'écriture dans la base de données MSXDBCDC. Entrez les informations d'identification pour une connexion qui a l'autorisation d'écriture dans la base de données MSXDBCDC, telle qu'un membre du rôle `sysasmin` .  
  
### Options  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion** : tapez le délai (en secondes) pendant lequel le service de capture de données modifiées pour Oracle attend une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant expiration. La valeur par défaut est **15**.  
  
-   **Délai d’exécution** : tapez le délai (en secondes) pendant lequel le service Windows de capture de données modifiées Oracle attend l’exécution d’une commande avant expiration. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: sélectionnez **Chiffrer la connexion** pour la communication entre le service de capture de données modifiées Oracle et l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible à l'aide d'une connexion chiffrée.  
  
-   **Avancé**: tapez des propriétés de connexion supplémentaires, si nécessaire.  
  
### Afficher le script  
 Cliquez sur **Afficher le script** pour afficher une version en lecture seule du script d’installation. Un administrateur système [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut copier ce script dans la console de gestion SQL Server en vue de le modifier et de l'exécuter, si nécessaire. Pour plus d’informations sur le script Préparer SQL Server, consultez [Préparer SQL Server pour Oracle CDC : afficher le script](../../integration-services/change-data-capture/prepare-sql-server-for-oracle-cdc-view-script.md).  
  
## Voir aussi  
 [Procédure : utiliser des services de capture de données modifiées](../../integration-services/change-data-capture/how-to-work-with-cdc-services.md)   
 [Procédure : préparer SQL Server pour la capture de données modifiées](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)  
  
  