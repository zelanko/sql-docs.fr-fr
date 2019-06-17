---
title: 'Utiliser des fonctions : SQL Server Machine Learning Services de profilage de code R'
description: Améliorer les performances et obtenir des résultats plus rapidement sur des calculs R sur SQL Server à l’aide de fonctions de profilage de R pour retourner des informations sur les appels de fonction interne.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c9195a6c2b9a2192e9d8fd04ce3e5d2592b1b23e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62642256"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Utiliser des fonctions de profilage de code R pour améliorer les performances
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

En plus des ressources et des outils SQL Server permettant de surveiller l’exécution de script R, vous pouvez utiliser les outils de performances fournis par d’autres packages R pour obtenir des informations complémentaires sur les appels de fonctions internes. 

> [!TIP]
> Cet article fournit des ressources de base pour vous aider à démarrer. Pour des conseils d’experts, nous vous recommandons du *performances* section [« Advanced R » par Hadley Wickham](http://adv-r.had.co.nz).

## <a name="using-rprof"></a>Utilisation de RPROF

[*rprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) est une fonction incluse dans le package de base [ **utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1), qui est chargé par défaut. 

En général, la fonction *rprof* opère en écrivant la pile d’appels dans un fichier selon des intervalles définis. Vous pouvez ensuite utiliser le [ *summaryRprof* ](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) fonction pour traiter le fichier de sortie. L’un des avantages de la fonction *rprof* est qu’elle effectue un échantillonnage, ce qui atténue la charge de performances de la surveillance.

Pour utiliser le profilage R dans votre code, vous devez appeler cette fonction et spécifier ses paramètres, notamment le nom de l’emplacement du fichier journal qui sera écrit. Le profilage peut être activé et désactivé dans le code. La syntaxe suivante illustre l’utilisation de base : 

```R
# Specify profiling output file.
varOutputFile <- "C:/TEMP/run001.log")
Rprof(varOutputFile)

# Turn off profiling
Rprof(NULL)
    
# Restart profiling
Rprof(append=TRUE)
```

> [!NOTE]
> Pour pouvoir utiliser cette fonction, vous devez installer Windows Perl sur l’ordinateur appelé à exécuter le code. Par conséquent, nous recommandons de profiler le code pendant la phase de développement dans un environnement R, puis de déployer le code débogué sur SQL Server.  


## <a name="r-system-functions"></a>Fonctions du système R

Le langage R intègre la plupart des fonctions du package de base qui retournent le contenu des variables système. Par exemple, dans votre code R, vous pouvez utiliser `Sys.timezone` pour obtenir le fuseau horaire actuel ou `Sys.Time` pour obtenir l’heure système à partir de R. 

Pour obtenir des informations sur les différentes fonctions du système R, tapez le nom de la fonction comme argument de la fonction `help()` R à partir d’une invite de commandes R.

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>Débogage et profilage dans R

La documentation de Microsoft R Open, qui est installé par défaut, vous trouverez un manuel sur le développement d’extensions pour le langage R qui traite [profilage et de débogage](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging) en détail. Vous trouverez la documentation de même sur votre ordinateur à C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>Voir aussi

+ [package utils R](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ [« Advanced R » par Hadley Wickham](http://adv-r.had.co.nz)
