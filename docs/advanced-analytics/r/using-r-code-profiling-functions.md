---
title: Utiliser les fonctions de profilage de code R
description: Améliorez les performances et bénéficiez de résultats plus rapides sur les calculs R sur SQL Server à l’aide des fonctions de profilage R pour retourner des informations sur les appels de fonction internes.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/12/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e03ae1a8c4cdab87f46f63da6271886b4518b5e3
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715014"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Utiliser des fonctions de profilage de code R pour améliorer les performances
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

En plus des ressources et des outils SQL Server permettant de surveiller l’exécution de script R, vous pouvez utiliser les outils de performances fournis par d’autres packages R pour obtenir des informations complémentaires sur les appels de fonctions internes. 

> [!TIP]
> Cet article fournit des ressources de base pour vous aider à démarrer. Pour obtenir des conseils d’experts, nous vous recommandons d’utiliser la section *performance* de [«avancé R» de Hadley Wickham](http://adv-r.had.co.nz).

## <a name="using-rprof"></a>Utilisation de RPROF

[*rprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) est une fonction incluse dans l' [**utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1)de package de base, qui est chargé par défaut. 

En général, la fonction *rprof* opère en écrivant la pile d’appels dans un fichier selon des intervalles définis. Vous pouvez ensuite utiliser la fonction [*summaryRprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) pour traiter le fichier de sortie. L’un des avantages de la fonction *rprof* est qu’elle effectue un échantillonnage, ce qui atténue la charge de performances de la surveillance.

Pour utiliser le profilage R dans votre code, vous devez appeler cette fonction et spécifier ses paramètres, notamment le nom de l’emplacement du fichier journal qui sera écrit. Le profilage peut être activé et désactivé dans le code. La syntaxe suivante illustre l’utilisation de base: 

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

La documentation de Microsoft R Open, qui est installée par défaut, comprend un manuel sur le développement d’extensions pour le langage R qui traite du [profilage et](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging) du débogage en détail. Vous trouverez la même documentation sur votre ordinateur dans C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>Voir aussi

+ [paquet R R](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ [«R avancé» par Hadley Wickham](http://adv-r.had.co.nz)
