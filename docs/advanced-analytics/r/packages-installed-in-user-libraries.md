---
title: Conseils pour l’utilisation de packages R sont installés dans les bibliothèques utilisateur - SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: e1aea5bd9166386662fc090a7a6d41737a9eecb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962568"
---
# <a name="tips-for-using-r-packages-in-sql-server"></a>Conseils d’utilisation des packages R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article comporte des sections séparées pour les bases de données qui ne sont pas familiarisés avec R et les développeurs expérimentés dans R, qui sont des accès de package inconnu dans une instance de SQL Server.

## <a name="new-to-r"></a>Vous débutez avec R

En tant qu’administrateur installation R packages pour la première fois, le fait de connaître quelques notions de base sur la gestion des packages R peuvent vous aider à commencer.

### <a name="package-dependencies"></a>Dépendances de package

Packages R dépendent souvent de plusieurs packages, certains d'entre eux soient pas disponibles dans la bibliothèque R par défaut utilisée par l’instance. Parfois, un package nécessite une version différente d’un package dépendant est déjà installé. Dépendances de package sont indiquées dans un fichier de DESCRIPTION incorporé dans le package, mais ne sont parfois pas complets. Vous pouvez utiliser un package appelé [iGraph](https://igraph.org/r/) entièrement expliquer le graphique de dépendance.

Si vous avez besoin installer plusieurs packages, ou vous assurer que tous les membres de votre organisation Obtient le type de package approprié et la version, nous vous recommandons d’utiliser le [miniCRAN](https://mran.microsoft.com/package/miniCRAN) package pour analyser la chaîne de dépendance complet. minicRAN crée un référentiel local qui peut être partagé entre plusieurs utilisateurs ou ordinateurs. Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="package-sources-versions-and-formats"></a>Formats, les versions et les sources de package

Il existe plusieurs sources de packages R, telles que [CRAN](https://cran.r-project.org/) et [Bioconductor](https://www.bioconductor.org/). Le site officiel pour le langage R (<https://www.r-project.org/>) répertorie la plupart de ces ressources. Microsoft propose [MRAN](https://mran.microsoft.com/) pour sa distribution de R open source ([MRO](https://mran.microsoft.com/open)) et d’autres packages. De nombreux packages sont publiés sur GitHub, où les développeurs peuvent obtenir le code source.

Packages de R s’exécutent sur plusieurs plates-formes informatiques. N’oubliez pas que les versions que vous installez sont les fichiers binaires Windows.

### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Connaître la bibliothèque dans laquelle vous effectuez l’installation et les packages déjà installés.

Si vous avez déjà modifié l’environnement R sur l’ordinateur, avant d’installer quoi que ce soit, vérifiez que la variable d’environnement R `.libPath` utilise qu’un seul chemin d’accès.

Ce chemin d’accès doit pointer vers le dossier R_SERVICES de l’instance. Pour plus d’informations, notamment comment déterminer quels packages sont déjà installés, consultez [packages par défaut de R et Python dans SQL Server](../package-management/default-packages.md).

## <a name="new-to-sql-server"></a>Nouveauté pour SQL Server

En tant que R développeur travaillant sur le code qui s’exécute sur SQL Server, les stratégies de sécurité protège le serveur limitent votre capacité à contrôler l’environnement R.

### <a name="r-user-libraries-not-supported-on-sql-server"></a>Bibliothèques d’utilisateur R : non pris en charge sur SQL Server

Les développeurs R qui ont besoin d’installer de nouveaux packages R sont habitués à l’installation des packages à volonté, à l’aide d’un privé, la bibliothèque de l’utilisateur chaque fois que la bibliothèque par défaut n’est pas disponible, ou lorsque le développeur n’est pas un administrateur sur l’ordinateur. Par exemple, dans un environnement de développement R standard, l’utilisateur voulez-vous ajouter l’emplacement du package à la variable d’environnement R `libPath`, ou référencer le chemin d’accès complet du package, comme suit :

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Cela ne fonctionne pas lors de l’exécution des solutions R dans SQL Server, étant donné que les packages R doivent être installés dans une bibliothèque spécifique par défaut qui est associée à l’instance. Lorsqu’un package n’est pas disponible dans la bibliothèque par défaut, vous obtenez cette erreur lorsque vous essayez d’appeler le package :

*Erreur dans xxx : il n’existe aucun package appelé « package-name »*

### <a name="avoid-package-not-found-errors"></a>Éviter les erreurs de « package introuvable »

+ Éliminer les dépendances sur les bibliothèques utilisateur. 

    Il est une pratique de développement incorrecte pour installer les packages R requis dans une bibliothèque utilisateur personnalisée, comme il peut entraîner des erreurs si une solution est exécutée par un autre utilisateur qui n’a pas accès à l’emplacement de la bibliothèque.

    En outre, si un package est installé dans la bibliothèque par défaut, le runtime R charge le package à partir de la bibliothèque par défaut, même si vous spécifiez une version différente dans le code R.

+ Modifier votre code s’exécute dans un environnement partagé.

+ Évitez d’installer des packages dans le cadre d’une solution. Si vous n’êtes autorisé à installer des packages, le code échoue. Même si vous disposez des autorisations pour installer des packages, vous devez le faire séparément du reste du code que vous souhaitez exécuter.

+ Vérifiez votre code pour vous assurer qu’il ne contient pas d’appel à des packages désinstallés.

+ Mettre à jour votre code pour supprimer des références directes aux chemins des packages R ou les bibliothèques R. 

+ Savoir quelle bibliothèque de package est associée à l’instance. Pour plus d’informations, consultez [packages par défaut de R et Python dans SQL Server](../package-management/default-packages.md).

## <a name="see-also"></a>Voir aussi

+ [Installer de nouveaux packages R](install-additional-r-packages-on-sql-server.md)
+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Didacticiels, exemples, solutions](../tutorials/machine-learning-services-tutorials.md)