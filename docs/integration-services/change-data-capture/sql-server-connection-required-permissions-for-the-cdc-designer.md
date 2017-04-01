---
title: "Autorisations de connexion SQL Server requises pour le concepteur CDC | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80334de2-17c1-43c9-951e-21a9f864e9cb
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Autorisations de connexion SQL Server requises pour le concepteur CDC
  La console du concepteur CDC nécessite des informations de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour effectuer ses tâches. Cette rubrique décrit les informations qui peuvent être fournies dans la boîte de dialogue **Connexion à SQL Server** pour configurer la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La boîte de dialogue **Connexion à SQL Server** s'affiche si nécessaire, par exemple lorsque les informations de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas disponibles ou lorsque les informations existent mais que la connexion ne dispose pas des autorisations nécessaires.  
  
 Le tableau suivant décrit les différentes tâches où une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est requise et les autorisations requises de la connexion ou de l’utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Tâche|Autorisations minimales|  
|----------|-------------------------|  
|Afficher la liste des services et des instances de capture de données modifiées à l'aide de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associée.|`db_datareader` sur MSXDBCDC|  
|Démarrer/arrêter une ou plusieurs instances de capture de données modifiées|`db_datareader` et `db_datawriter` sur MSXDBCDC|  
|Afficher l'état d'instance de capture de données modifiées.|`db_owner` sur la base de données d'instance de capture de données modifiées|  
|Créer une base de données d'instance Oracle CDC.|`dbcreator` Rôle serveur fixe|  
|Créer une instance Oracle CDC.|`db_datareader` sur MSXDBCDC<br /><br /> `db_owner` sur la base de données CDC créée.|  
|Obtenir des scripts de déploiement.|`db_datareader` et `db_datawriter` sur MSXDBCDC<br /><br /> `db_owner` sur la base de données CDC associée|  
|Modifier la configuration et ajouter/supprimer des instances de capture.|`db_datareader` et `db_datawriter` sur MSXDBCDC<br /><br /> `db_owner` sur la base de données CDC associée|  
  
## Voir aussi  
 [Accéder à la console du concepteur CDC](../../integration-services/change-data-capture/access-the-cdc-designer-console.md)   
 [Connexion SQL Server pour la création d'une instance](../../integration-services/change-data-capture/sql-server-connection-for-instance-creation.md)  
  
  