---
title: "Configurer un client de science des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Configurer un client de science des donn&#233;es
  Après avoir configuré une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] en installant **R Services (dans la base de données)**, vous pourrez configurer un environnement de développement R capable de se connecter au serveur pour le déploiement et l’exécution à distance. 
  
  Votre environnement client doit inclure Microsoft R Open, ainsi que les packages RevoScaleR supplémentaires qui prennent en charge l’exécution distribuée de R sur SQL Server.  Il existe plusieurs méthodes d’installation de ces packages :
  
+ Installez [Microsoft R Open](http://aka.ms/rclient/download).
+ Installez Microsoft R Server. Vous pouvez obtenir Microsoft R Server à partir de la configuration SQL Server ou d’un programme d’installation autonome. Pour plus d’informations, consultez [Créer un R Server autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md) ou [Introduction à R Server](https://msdnstage.redmond.corp.microsoft.com/en-us/microsoft-r/rserver?branch=r-server-nov16-dev).

 Pour plus d’informations sur l’utilisation de Microsoft R Client pour la connexion à SQL Server à l’aide de packages ScaleR, consultez [Prise en main de ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#).  
  
 Pour une description détaillée de la connexion à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’exécution distante du code R, consultez ce didacticiel : [Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer SQL Server R Services &#40;dans la base de données&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  