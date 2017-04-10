---
title: "Modifier le pool de comptes d’utilisateurs pour SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Modifier le pool de comptes d’utilisateurs pour SQL Server R Services
  Dans le cadre du processus d’installation pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], une nouvelle fenêtre *pool de compte d’utilisateur* est créé pour prendre en charge l’exécution de tâches par le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service. L’objectif de ces comptes de travail consiste à isoler l’exécution simultanée de Scripts R par différents utilisateurs SQL.
  
  Le nombre de comptes d’utilisateurs figurant dans ce pool détermine le nombre de sessions R qui peuvent être actives simultanément.   Si le même utilisateur exécute simultanément plusieurs scripts R, toutes les sessions sont exécutées par l’utilisateur utilise le même compte de travail. Par conséquent, un utilisateur unique peut avoir 100 différents scripts R exécutées simultanément tant que permettent les ressources.

## Configuration par défaut   
-   Dans une instance par défaut, le nom du groupe est **SQLRUserGroup**. 
-   Dans une instance nommée, le nom du groupe par défaut est avec le suffixe du nom de l’instance : par exemple, **SQLRUserGroupMyInstanceName**. 
-   Comptes : Par défaut, le pool de compte d’utilisateur contient 20 comptes d’utilisateurs nommés **MSSQLSERVER01** via **MSSQLSERVER20** pour l’instance par défaut.  
-   Pour une instance nommée, les comptes d’utilisateurs sont nommés en utilisant le nom de l’instance : par exemple, **MyInstanceName01** via **MyInstanceName20**.  


## Gérer le groupe d’utilisateurs pour chaque Instance
Le groupe de compte Windows est créé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation pour chaque instance sur lequel R Services est installé, si vous avez installé plusieurs instances qui prennent en charge R, il y aura plusieurs groupes d’utilisateurs.
Toutefois, chaque groupe d’utilisateurs est associé le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service sur une instance spécifique et ne peut pas prendre en charge les travaux R qui s’exécutent sur d’autres instances.

Par défaut, le groupe ne **pas** ont des autorisations de connexion le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance auquel il est associé. Si vous avez besoin de permettre l’exécution de scripts R par les utilisateurs, l’administrateur de base de données doit fournir ce groupe avec **se connecter à** autorisations.  

### Modification du nombre de comptes de travail dans le groupe d’utilisateurs Windows

Pour modifier le nombre d’utilisateurs dans le pool de compte, vous devez modifier les propriétés de la [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] service tel que décrit ci-dessous.  
  
Mots de passe associés à chaque compte d’utilisateur sont générés de manière aléatoire, mais vous pouvez les modifier ultérieurement une fois que les comptes sont créés.  
  
1. Ouvrez le Gestionnaire de Configuration SQL Server, puis sélectionnez **Services SQL Server**.
2. Double-cliquez sur le service SQL Server Launchpad et arrêtez le service s’il est en cours d’exécution. 
3.  Sur le **Service** onglet, vérifiez que le Mode de démarrage est défini sur automatique. Le script R échoue si le LaunchPad n’est pas en cours d’exécution.
4.  Cliquez sur le **Avancé** onglet et modifier la valeur de **nombre d’utilisateurs externes** si nécessaire. Ce paramètre contrôle le nombre d’utilisateurs différents SQL peuvent exécuter des requêtes simultanément R. La valeur par défaut est 20 comptes, ce qui, dans la plupart des cas est largement suffisant prendre en charge des sessions de R.
5. Si vous le souhaitez, vous pouvez définir l’option **de réinitialisation de mot de passe aux utilisateurs externes** à _Oui_ Si votre organisation dispose d’une stratégie qui requiert la modification des mots de passe tous les 90 jours. Cette opération va être régénérée les mots de passe chiffrés LaunchPad gère les comptes d’utilisateur.    
6.  Redémarrage du service.  

## Autorisations supplémentaires nécessaires pour l’exécution de scripts à distance
Si vous exécutez le script R à l’ordinateur SQL Server comme une référence distante calcul contexte, ce groupe de travail nécessite une autorisation pour se connecter à l’instance de SQL Server dans lequel les scripts R sont exécutés.

Pour plus d’informations, consultez [FAQ sur la mise à niveau et l’installation](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md). 

  
## Voir aussi  
 [Configuration (SQL Server R Services)](../../advanced-analytics/r-services/configuration-sql-server-r-services.md)
  