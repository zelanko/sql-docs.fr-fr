---
title: "Conditions pr&#233;alables pour les proc&#233;dures pas &#224; pas de science de donn&#233;es (SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# Conditions pr&#233;alables pour les proc&#233;dures pas &#224; pas de science de donn&#233;es (SQL Server R Services)
Nous vous recommandons d’effectuer les procédures pas à pas sur une station de travail R qui peut se connecter à un ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le même réseau. Vous pouvez également exécuter la procédure pas à pas sur un ordinateur qui a à la fois [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l’environnement de développement R. 
  
  
## <a name="install-sql-server-2016-r-services-in-database"></a>Installer SQL Server 2016 R Services (en base de données)  
Vous devez avoir accès à une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] installé. Pour plus d’informations sur la configuration de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], consultez [Configurer SQL Server R Services (en base de données)](https://msdn.microsoft.com/library/mt696069.aspx).  
  
  
> [!IMPORTANT]  
> Veillez à utiliser [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou version ultérieure. Les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prennent pas en charge l’intégration à R, mais vous pouvez utiliser des bases de données SQL de version antérieure comme source de données ODBC.  
  
## <a name="install-an-r-development-environment"></a>Installer un environnement de développement R  
Pour effectuer cette procédure pas à pas sur votre ordinateur, vous avez besoin d’un environnement de développement R, ou de tout autre outil en ligne de commande qui peut exécuter des commandes R.    
  
- Les**Outils R pour Visual Studio** sont un plug-in gratuit qui fournit Intellisense, des fonctionnalités de débogage et la prise en charge de Microsoft R Server et de SQL Server R Services. Pour télécharger, consultez [Outils R pour Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx).  
    
- **Microsoft R Client** est un outil de développement léger qui prend en charge le développement dans R à l’aide de packages ScaleR. Pour l’obtenir, consultez [Get Started with Microsoft R Client (Prise en main de Microsoft R Client)](https://msdn.microsoft.com/microsoft-r/r-client-get-started).
  
- **RStudio** est un des environnements les plus populaires pour le développement R. Pour plus d’informations, consultez [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/).  
  
    Toutefois, vous ne pouvez pas suivre ce didacticiel à l’aide d’une installation générique de RStudio ou d’un autre environnement ; vous devez également installer les packages R et les bibliothèques de connectivité pour Microsoft R Open. Pour plus d’informations, consultez [Configurer un client de science des données](https://msdn.microsoft.com/library/mt696067.aspx).  

- Les outils R (R.exe, RTerm.exe, RScripts.exe) sont installés par défaut quand vous installez [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]. Si vous ne souhaitez pas installer un IDE, vous pouvez utiliser ces outils.  
  
  
## <a name="get-permissions-to-connect-to-sql-server"></a>Obtenir des autorisations de se connecter à SQL Server  
Dans cette procédure pas à pas, vous allez vous connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour exécuter des scripts et charger des données. Pour ce faire, vous devez disposer d’une connexion valide sur le serveur de base de données.  Vous pouvez utiliser un compte de connexion SQL ou l’authentification Windows intégrée. Demandez à l’administrateur de base de données de créer un compte pour vous sur le serveur avec les droits ci-après sur la base de données où vous utiliserez R :  
  
-   Créer une base de données, des tables, des fonctions et des procédures stockées    
-   Insérer des données dans les tables  
  
  
## <a name="start-the-walkthrough"></a>Démarrer la procédure pas à pas  
[Leçon 1 : Préparer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
