---
title: Amélioration des performances avec la fonction de profilage de code R
description: Recueillez des informations utiles pour améliorer les performances et bénéficier de résultats de calcul R plus rapides sur SQL Server avec des fonctions de profilage R. La fonction *rprof* collecte et retourne des informations sur les appels de fonction internes.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 12/12/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e65171fa0222c0c581f692bede727dc4366c9c53
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180436"
---
# <a name="use-r-code-profiling-functions-to-improve-performance"></a>Utiliser les fonctions de profilage de code R pour améliorer les performances
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

En plus des ressources et des outils SQL Server permettant de surveiller l’exécution de script R, vous pouvez utiliser les outils de performances fournis par d’autres packages R pour obtenir des informations complémentaires sur les appels de fonctions internes. 

> [!TIP]
> Cet article fournit des ressources de base pour vous aider à démarrer. Pour obtenir des conseils d’expert, nous vous recommandons de lire la section *Performance* de l’ouvrage de [Hadley Wickham, « Advanced R »](http://adv-r.had.co.nz).

## <a name="using-rprof"></a>Utilisation de RPROF

[*rprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/Rprof) est une fonction intégrée au package de base [**utils**](https://www.rdocumentation.org/packages/utils/versions/3.5.1), qui est chargé par défaut. 

En général, la fonction *rprof* opère en écrivant la pile d’appels dans un fichier selon des intervalles définis. Vous pouvez ensuite utiliser la fonction [*summaryRprof*](https://www.rdocumentation.org/packages/utils/versions/3.5.1/topics/summaryRprof) pour traiter le fichier de sortie. L’un des avantages de la fonction *rprof* est qu’elle effectue un échantillonnage, ce qui atténue la charge de performances de la surveillance.

Pour utiliser le profilage R dans votre code, vous devez appeler cette fonction et spécifier ses paramètres, notamment le nom de l’emplacement du fichier journal qui sera écrit. Le profilage peut être activé et désactivé dans le code. La syntaxe suivante illustre l’utilisation de base : 

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

Dans la documentation de Microsoft R Open, qui est installée par défaut, vous trouverez un manuel sur le développement d’extensions pour le langage R qui traite en détail [du profilage et du débogage](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging). Vous trouverez la même documentation sur votre ordinateur, sous C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\doc\manual.

## <a name="see-also"></a>Voir aussi

+ [Package R utils](https://www.rdocumentation.org/packages/utils/versions/3.5.1)
+ [« Advanced R » par Hadley Wickham](http://adv-r.had.co.nz)
