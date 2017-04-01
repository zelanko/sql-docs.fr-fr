---
title: "Consid&#233;rations relatives &#224; la s&#233;curit&#233; pour le composant d’ex&#233;cution R dans SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5065197-69e6-4fce-9654-00acaecc148b
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 15
---
# Consid&#233;rations relatives &#224; la s&#233;curit&#233; pour le composant d’ex&#233;cution R dans SQL Server
  Cette rubrique fournit une vue d’ensemble des considérations relatives à la sécurité lors de l’utilisation de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Pour plus d’informations sur la gestion du service et la mise en service des comptes d’utilisateur utilisés pour exécuter des scripts R, consultez [Configure and Manage Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md).  
  
## Utiliser le pare-feu pour restreindre l’accès réseau via le composant d’exécution R  
 Dans la méthode d’installation suggérée, une règle de pare-feu Windows est utilisée pour bloquer tout accès réseau sortant des processus d’exécution R. Des règles de pare-feu doivent être créées pour éviter que le processus d’exécution R ne télécharge des packages ou n’effectue d’autres appels réseau potentiellement malveillants.  
  
 Nous vous recommandons vivement d’activer le pare-feu Windows (ou un autre pare-feu de votre choix) pour bloquer l’accès réseau via le composant d’exécution R.  
  
 Si vous utilisez un autre programme de pare-feu, vous pouvez également créer des règles pour bloquer les connexions réseau sortantes pour le composant d’exécution R en définissant des règles pour les comptes d’utilisateurs locaux ou pour le groupe représenté par le pool de comptes d’utilisateur.   
Pour plus d’informations, consultez [Configure and Manage Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md).  
  
## Méthodes d’authentification prises en charge pour les contextes de calcul à distance 
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] prend désormais en charge les connexions à la fois l’authentification intégrée Windows et SQL lors de la création de connexions entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et un client de science des données distantes. 
  
 Par exemple, si vous développez une solution de R sur votre ordinateur portable et que vous souhaitez effectuer des calculs sur l’ordinateur SQL Server, vous devez créer une source de données SQL Server dans R, à l’aide de la **rx** fonctions et en définissant une chaîne de connexion en fonction de vos informations d’identification Windows. Lorsque vous modifiez le _contexte de calcul_ à partir de votre ordinateur portable à l’ordinateur SQL Server, si votre compte Windows dispose des autorisations nécessaires, tout le code R s’exécutera sur l’ordinateur SQL Server. En outre, toutes les requêtes SQL exécutées dans le cadre du code R s’exécutera sous également vos informations d’identification. 
 
 Bien qu’une connexion SQL peut également servir dans la chaîne de connexion pour une source de données SQL Server, l’utilisation d’une connexion requiert que l’instance de SQL Server permettent l’authentification en mode mixte.
 
 ### Authentification implicite
  
 En règle générale le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] démarre le runtime R et exécute les scripts R sous son propre compte. Toutefois, si le script R effectue un appel ODBC, le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] empruntera les informations d’identification de l’utilisateur qui a envoyé la commande pour vous assurer que l’appel ODBC n’échoue pas. Il s’agit *authentification implicite*. 
 
 > [!IMPORTANT] 
 >
 > Pour l’authentification implicite réussisse, le groupe d’utilisateurs Windows qui contient les comptes de travail (par défaut, **SQLRUser**) doit avoir un compte dans la base de données master pour l’instance et ce compte doivent disposer d’autorisations pour se connecter à l’instance.  
  
## Chiffrement au repos non pris en charge  
 La fonctionnalité Transparent Data Encryption n’est pas prise en charge pour les données reçues ou transmises par le composant d’exécution R. Par conséquent, le chiffrement au repos **ne s’appliquera** à aucune donnée utilisée dans les scripts R, à aucune donnée enregistrée sur le disque, ni à aucun résultat intermédiaire persistant.  
 
 ## Voir aussi
 [Entrez la description du lien ici](../../advanced-analytics/r-services/configuration-sql-server-r-services.md) 
  