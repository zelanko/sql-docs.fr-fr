---
title: "Configurer un client de science des données | Microsoft Docs"
ms.custom: 
ms.date: 02/10/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0661b2fcf9b23d3c81cb0d80f0424d87dbde7ef8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-up--a-data-science-client"></a>Configurer un client de science des données
  Après avoir configuré une instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] en installant **R Services (dans la base de données)**, vous pourrez configurer un environnement de développement R capable de se connecter au serveur pour le déploiement et l’exécution à distance. 
  
  Cet environnement doit inclure les packages ScaleR et, éventuellement, un environnement de développement client.
  
 ## <a name="where-to-get-scaler"></a>Où obtenir ScaleR 
  
  Votre environnement client doit inclure Microsoft R Open, ainsi que les packages RevoScaleR supplémentaires qui prennent en charge l’exécution distribuée de R sur SQL Server.  Il existe plusieurs méthodes d’installation de ces packages :
  
+ Installez [Microsoft R Open](http://aka.ms/rclient/download). Pour obtenir des instructions d’installation supplémentaires, consultez [Get Started with Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started) (Bien démarrer avec Microsoft R Client).
+ Installez Microsoft R Server. Vous pouvez obtenir Microsoft R Server à partir du programme d’installation de SQL Server, ou en utilisant le nouveau programme d’installation de Windows en mode autonome. Pour plus d’informations, consultez [Créer un serveur R autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md) et [Introduction à R Server](https://msdn.microsoft.com/microsoft-r/rserver).

Si vous avez un contrat de licence R Server, nous vous recommandons d’utiliser Microsoft R Server (autonome) pour éviter les limitations de R relatives au traitement des threads et des données en mémoire.


## <a name="how-to-set-up-the-r-development-environment"></a>Comment configurer l’environnement de développement R

Vous pouvez utiliser n’importe quel environnement de développement R qui est compatible avec Windows. 

+ Le complément Outils R pour Visual Studio prend en charge l’intégration avec Microsoft R Open.
+ RStudio est un environnement gratuit couramment utilisé.  

Après l’installation, vous devrez reconfigurer votre environnement pour utiliser les bibliothèques Microsoft R Open par défaut. Sinon, vous n’aurez pas accès aux bibliothèques ScaleR. Pour plus d’informations, consultez [Getting Started with Microsoft R Client](http://msdn.microsoft.com/microsoft-r/r-client-get-started) (Bien démarrer avec Microsoft R Client).
 
## <a name="more-resources"></a>Plus de ressources
  
 Pour une description détaillée de la connexion à une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’exécution distante du code R, consultez ce didacticiel : [Immersion dans la science des données : utilisation des packages RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md).  
 

Pour commencer à utiliser Microsoft R Client et les packages ScaleR avec SQL Server, consultez [ScaleR Getting Started](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#) (Bien démarrer avec ScaleR).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer SQL Server R Services &#40;dans la base de données&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  

