---
title: "Le programme d’installation ou de configurer les outils R | Microsoft Docs"
ms.custom: ""
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Le programme d’installation ou de configurer les outils R
  Microsoft R Server fournit toutes les bibliothèques R de base, les packages de mise à l’échelle R et les outils R standards dont vous avez besoin pour développer et tester le code R. Toutefois, si vous souhaitez utiliser un environnement de développement R dédié, il existe plusieurs disponibles, y compris plusieurs outils gratuits.  
  
## <a name="basic-r-tools"></a>Outils de base R  
 Outils supplémentaires ne sont pas nécessaires dans une installation de Microsoft R Server, car tous le R standard des outils qui sont inclus dans une *installation de base* de R sont installés par défaut.

-   **RTerm**: un outil de ligne de commande pour l’exécution de scripts R 
  
-   **RGui.exe**: un simple éditeur interactif pour R. Les arguments de ligne de commande sont les mêmes pour RGui.exe et RTerm. 
  
-   **RScript**: un outil de ligne de commande pour R en cours d’exécution de scripts en mode batch.  

Par défaut, ces outils sont installés dans les dossiers suivants :
- SQL Server 2016 : `C:\Program Files\Microsoft SQL Server\130\R_SERVER\bin\x64`  
- SQL Server vNext : `C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64`  

> [!TIP]  
>  Besoin d’aide ? Vous trouverez la documentation pour les outils R dans le dossier d’installation : `C:\Program Files\Microsoft SQL Server\R_SERVER\doc` et `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual`.  
>   
>  Ou, il suffit d’ouvrir **RGui**, cliquez sur **aide**, puis sélectionnez une des options.  

## <a name="microsoft-r-client"></a>Microsoft R Client

Le Client Microsoft R est un téléchargement gratuit qui vous permet de développer des solutions R qui peuvent être facilement exécutées dans Microsoft R Server ou SQL Server Services R.

En général, vous avez installer un autre environnement de développement R, telles que les outils R pour Visual Studio ou RStudio et que le Client de R Microsoft utilisé en tant que l’exécutable de R. Cela vous donne un accès complet au package RevoScaleR et d’autres fonctionnalités de Microsoft R Server.

Vous pouvez également utiliser des outils familiers tels que RGui et RTerm pour exécuter des scripts ou d’écrire et d’exécuter du code R ad hoc.

[Installer le Client de Microsoft R](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="a-namebkmkrtoolsa-r-tools-for-visual-studio"></a> Outils R pour Visual Studio  

 Pour plus de commodité dans l’utilisation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données, envisagez d’utiliser [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] comme environnement de développement. [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] est un complément gratuit de Visual Studio qui fonctionne dans toutes les éditions de Visual Studio. Visual Studio fournit également la prise en charge pour l’intégration de Python et F #.  

Pour plus d’informations, consultez [VisualStudio.com](https://www.visualstudio.com/vs/rtvs/).

 Cette section décrit comment installer [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] à l’aide de la libre Community Edition de Visual Studio.  
  
#### <a name="install-visual-studio"></a>Installer Visual Studio  
  
1.  L’édition de communauté gratuite de Visual Studio est disponible en téléchargement à partir de cette page : [Visual Studio Community](http://visualstudio.com/products/visual-studio-community-vs.aspx)  
  
2.  Une fois le téléchargement terminé, cliquez sur **exécuter** et sélectionnez les composants à installer.  
  
     Si vous effectuez une installation personnalisée, notez que les composants de Microsoft Web Developer sont requises.  
  
3.  Choisissez le **Général** définition pour le moment. Lorsque vous installez [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)], vous aurez la toption pour passer à une disposition personnalisée pour le développement de R.  

#### <a name="add-the-r-tools"></a>Ajouter les outils R

Une fois que Visual Studio est installé, les extensions sont disponibles pour R, Python et bien d’autres langues via la **Options** menu.

4. Cliquez sur outils dans la barre de menus, puis sélectionnez **Extensions et mises à jour**.

5. À la fin de l’installation, les outils R détecte les versions du runtime R sont disponibles sur l’ordinateur et demandez si vous souhaitez modifier votre environnement de développement pour utiliser le runtime R pour Microsoft R Server ou de l’exécution de R pour le Client Microsoft R.

Si le programme d’installation ne détecte pas l’exécution du serveur de R à utiliser, vous pouvez modifier manuellement à tout moment à l’aide de la **Options** menu. Pour plus d’informations, consultez [configurer de votre IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).

## <a name="rstudio"></a>RStudio

Si vous préférez utiliser RStudio, ces étapes supplémentaires pour utiliser les bibliothèques RevoScaleR :
- Installer Microsoft R serveur ou Client R de Microsoft pour obtenir les packages requis et les bibliothèques.
- Mettre à jour votre chemin d’accès de R pour utiliser le runtime R approprié.

Pour plus d’informations, consultez [configurer de votre IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide).


## <a name="see-also"></a>Voir aussi  
 [Créer un serveur de R autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Prise en main de Microsoft R Server &#40 ; Autonome &#41 ;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  