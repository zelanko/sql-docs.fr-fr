---
title: Prise en main de Microsoft R Server (autonome) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc7874c6900474c7c2f3d927183616b2f5e69699
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-microsoft-r-server-standalone"></a>Prise en main de Microsoft R Server (autonome)
  Microsoft R Server (autonome) vous permet de mettre en œuvre le langage R Open Source populaire dans votre entreprise pour permettre l’utilisation de solutions d’analyse hautes performances et l’intégration avec d’autres applications de gestion des informations professionnelles.  

  
## <a name="install-microsoft-r-server"></a>Installer Microsoft R Server 

Vous installez Microsoft R Server différemment selon que vous avez ou non besoin d’utiliser des données SQL Server dans vos applications. Si c’est le cas, vous devez utiliser le programme d’installation de SQL Server. Dans le cas contraire ou si vous n’avez pas besoin d’exécuter le code R en base de données, vous pouvez utiliser le programme d’installation de SQL Server ou le nouveau programme d’installation en mode autonome.
 
 
+ Installer Microsoft R Server (autonome) à partir du programme d’installation de SQL Server. Une instance distincte des fichiers binaires R est créée pour R Server et cette instance est concédée sous licence via la politique de support de SQL Server Enterprise Edition. Pour plus d’informations, consultez [Créer un serveur R autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  

+ Utilisez le nouveau programme d’installation Windows en mode autonome pour créer une nouvelle instance de Microsoft R Server qui utilise la politique de support du cycle de vie moderne des logiciels Microsoft. Pour plus d’informations, consultez [Exécuter Microsoft R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows).

+ Si vous voulez mettre à niveau une instance R Server (autonome) ou R Services, vous devez également télécharger et exécuter le programme d’installation Windows pour la mise à jour. Pour plus d’informations, consultez [Exécuter Microsoft R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows).
  
## <a name="install-additional-r-tools"></a>Installer des outils R supplémentaires  

 Nous vous recommandons la version gratuite de [Microsoft R Client](http://aka.ms/rclient/download) (télécharger).  

 Vous pouvez également utiliser votre environnement de développement R par défaut pour développer des solutions pour SQL Server R Services ou Microsoft R Server. Pour plus d’informations, consultez [Installer ou configurer les outils R](../../advanced-analytics/r-services/setup-or-configure-r-tools.md). 
 

### <a name="location-of-r-server-binaries"></a>Emplacement des fichiers binaires R Server

Selon la méthode que vous utilisez pour installer Microsoft R Server, l’emplacement par défaut est différent. Avant de commencer à utiliser votre environnement de développement par défaut, vérifiez l’emplacement d’installation des bibliothèques R :

+ Microsoft R Server installé à l’aide du nouveau programme d’installation Windows

  `C:\Program Files\Microsoft\R Server\R_SERVER`

+ R Server (autonome) installé via le programme d’installation de SQL Server

  `C:\Program Files\Microsoft SQL Server\130\R_SERVER`

+ R Services (dans la base de données)

  `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`
      
## <a name="start-using-r-on-microsoft-r-server"></a>Commencer à utiliser R sur Microsoft R Server  

 Après avoir installé les composants serveur et configuré votre IDE R pour utiliser les fichiers binaires R Server, vous pouvez commencer à développer votre solution en utilisant les nouvelles API, comme le package RevoScaleR, MicrosoftML et olapR.
    
Pour démarrer avec R Server, consultez ce guide dans la bibliothèque MSDN : [Get started with Microsoft R](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-node)   
  
-   [ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-getting-started) : explorez cet ensemble de fonctions analytiques distribuables qui offrent des performances élevées et la mise à l’échelle vers des solutions R. Inclut des versions parallélisables des packages de modélisation R les plus populaires comme le clustering k-means, les arbres de décision, les forêts de décision et les outils de manipulation des données. Pour plus d’informations, consultez [Explore R and ScaleR in 25 functions](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started-tutorial)  
    
- [MicrosoftML](https://msdn.microsoft.com/library/mt790482.aspx) : le package MicrosoftML est un ensemble de nouveaux algorithmes d’apprentissage automatique et transformations développés par Microsoft qui sont rapides et évolutifs. Pour plus d’informations, consultez [MicrosoftML: State-of-the-art machine learning R algorithms](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml).
  


  
## <a name="see-also"></a>Voir aussi  
 [Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  

