---
title: Installer ou configurer les outils R | Microsoft Docs
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3baf97a960d7e8f950bb6e9cd251550f4c4b942
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="setup-or-configure-r-tools"></a>Installer ou configurer les outils R
  Microsoft R Server fournit toutes les bibliothèques R de base, un ensemble de packages ScaleR et les outils R standard dont vous avez besoin pour développer et tester du code R. Toutefois, si vous souhaitez utiliser un environnement de développement R dédié, il existe d’autres outils disponibles, dont beaucoup sont gratuits.  
  
## <a name="basic-r-tools"></a>Outils R de base  
 Vous n’avez pas à installer d’outils supplémentaires dans une installation Microsoft R Server, car tous les outils R standard sont fournis dans l’*installation de base* de R et sont installés par défaut.

-   **RTerm** : outil en ligne de commande pour l’exécution de scripts R. 
  
-   **RGui.exe** : éditeur interactif simple pour R. Les arguments de ligne de commande sont les mêmes pour RGui.exe et RTerm. 
  
-   **RScript** : outil en ligne de commande pour l’exécution de scripts R en mode batch.  

Ces outils se trouvent à l’emplacement de la bibliothèque R. L’emplacement est différent selon que vous avez installé uniquement SQL Server R Services, ou installé également R Server (autonome). Pour plus d’informations, consultez [Quels sont les éléments installés et où trouver des packages R](https://msdn.microsoft.com/library/mt695941(sql.130).aspx#Anchor_1).

Recherchez ensuite les outils dans le dossier `..\R_SERVER\bin\x64`.  

> [!TIP]  
>  Si vous avez besoin d’aide pour utiliser les outils R, consultez la documentation fournie dans le dossier d’installation : `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` et dans `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual`.  
>   
>  Vous pouvez aussi simplement ouvrir **RGui**, cliquer sur **Aide**, puis sélectionner l’une des options proposées.  

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R Client est un outil que vous pouvez télécharger gratuitement. Il vous permet de développer des solutions R qui s’exécutent facilement dans Microsoft R Server ou SQL Server R Services. Cet outil est conçu pour aider les « scientifiques des données » qui n’ont pas R Server (disponible dans l’édition Enterprise) à développer des solutions utilisant ScaleR. 

Si vous utilisez un autre environnement de développement R (par exemple, Outils R pour Visual Studio ou RStudio) et souhaitez utiliser ScaleR, vous devez spécifier Microsoft R Client comme étant l’exécutable R. Ainsi, vous avez un accès total au package RevoScaleR et à d’autres fonctionnalités de Microsoft R Server (mais avec des performances réduites).

Vous pouvez également utiliser les outils fournis dans R Client, tels que RGui et RTerm, pour exécuter des scripts ou écrire et exécuter du code R ad hoc.

[Installer Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="bkmk_RTools"></a> Outils R pour Visual Studio  

 Pour simplifier votre travail avec des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)],utilisez de préférence [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] comme environnement de développement. [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] est un complément gratuit pour Visual Studio, compatible avec toutes les éditions de Visual Studio. Visual Studio prend également en charge l’intégration de Python et de F#.  

 Pour obtenir des instructions d’installation, consultez [comment installer les outils R pour Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).

> [!TIP]
> Avant d’installer de nouveaux packages, vérifiez quel runtime R est utilisé par défaut. Sinon, vous risquez d’installer de nouveaux packages R à un emplacement de bibliothèque par défaut et de ne pas réussir à les retrouver ensuite sur R Server.


## <a name="rstudio"></a>RStudio

Si vous préférez RStudio, vous devez effectuer des étapes supplémentaires pour pouvoir utiliser les bibliothèques RevoScaleR :
- Installez Microsoft R Server ou Microsoft R Client pour obtenir les packages et bibliothèques nécessaires.
- Mettez à jour votre chemin R pour utiliser le runtime R Server.

Pour plus d’informations, consultez [Configurer votre IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).


## <a name="see-also"></a>Voir aussi  
 [Créer un serveur R autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Bien démarrer avec Microsoft R Server &#40;autonome&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  

