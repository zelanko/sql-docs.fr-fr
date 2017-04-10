---
title: "&#192; l’aide des fonctions de profilage du Code R | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 132db249-b9f1-48f5-a63e-c9806cacc4af
caps.latest.revision: 6
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 5
---
# &#192; l’aide des fonctions de profilage du Code R
Outre l’utilisation des ressources de SQL Server et des outils pour surveiller l’exécution du script R, vous pouvez utiliser les outils de performance fournis par d’autres packages R pour obtenir plus d’informations sur les appels de fonction interne. Cette rubrique fournit une liste de certaines ressources de base pour vous aider à démarrer. Pour des conseils d’experts, nous recommandons le chapitre sur [performances](http://adv-r.had.co.nz/Performance.html) dans le livre « « Advanced R » », par Hadley Wickham.

## <a name="using-rprof"></a>À l’aide de RPROF

*rprof* est une fonction incluse dans le package de base **utils**, lequel est chargé par défaut. Un des avantages de *rprof* est qu’il effectue l’échantillonnage, ce qui diminue la charge de l’analyse.

Pour utiliser R profilage dans votre code, vous appelez cette fonction et spécifiez ses paramètres, y compris le nom de l’emplacement du fichier journal sera écrit. Consultez l’aide de *rprof* Pour plus d’informations.

En général, les *rprof* fonction fonctionne en écrivant la pile des appels dans un fichier, à des intervalles spécifiés. Vous pouvez ensuite utiliser le *summaryRprof* fonction pour traiter le fichier de sortie. 

Profilage permettre être activé et désactivées dans votre code. Pour activer le profilage, suspendez le profilage, puis redémarrez-la, vous utiliseriez une séquence d’appels à *rprof*:

1. Spécifiez le fichier de sortie de profilage.

    ```R
    varOutputFile <- "C:/TEMP/run001.log")
    Rprof(varOutputFile)
    ```
2. Désactivez le profilage
    ```R
    Rprof(NULL)
    ```
    
3. Redémarrez le profilage
    ```R
    Rprof(append=TRUE)
    ```


> [!NOTE] À l’aide de cette fonction nécessite que Windows Perl soit installé sur l’ordinateur où le code est exécuté. Par conséquent, nous recommandons que votre profiler du code pendant le développement dans un environnement R, puis déployez le code débogué sur SQL Server.  


## <a name="r-system-functions"></a>Fonctions système R

Le langage R inclut de nombreuses fonctions de module de base pour retourner le contenu des variables système. 

Par exemple, dans le cadre de votre code R, vous pouvez utiliser `Sys.timezone` pour obtenir le fuseau horaire actuel, ou `Sys.Time` pour obtenir l’heure système de R. 

Pour obtenir des informations sur les différentes fonctions du système R, tapez le nom de fonction comme argument à R `help()` fonction à partir d’une invite de commandes de R.

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>Débogage et profilage dans R

La documentation de Microsoft R Open, qui est installé par défaut, inclut un manuel sur le développement d’extensions du langage R qui traite de profilage et de débogage en détail.

Le chapitre est également disponible en ligne : [https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)

### <a name="location-of-r-help-files"></a>Emplacement des fichiers d’aide de R

C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\doc\manual


