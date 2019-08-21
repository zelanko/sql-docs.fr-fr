---
title: Conseils pour l’utilisation de packages R
description: Découvrez des conseils utiles sur l’utilisation des packages R dans SQL Server pour ceux qui débutent avec R ou SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/06/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5e283ab478a6d65243e9962fd5c26f5f91d87c15
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69633622"
---
# <a name="tips-for-using-r-packages"></a>Conseils pour l’utilisation de packages R

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fournit des conseils utiles sur l’utilisation des packages R dans SQL Server. Ces astuces sont destinées aux administrateurs de bases de connaissances qui ne sont pas familiarisés avec R et aux développeurs expérimentés qui ne connaissent pas l’accès aux packages dans une instance SQL Server.

## <a name="if-youre-new-to-r"></a>Si vous débutez avec R

En tant qu’administrateur qui installe les packages R pour la première fois, le fait de connaître quelques notions de base sur la gestion des packages R peut vous aider à commencer.

### <a name="package-dependencies"></a>Dépendances de package

Les packages R dépendent souvent de plusieurs autres packages, dont certains peuvent ne pas être disponibles dans la bibliothèque R par défaut utilisée par l’instance. Parfois, un package requiert une version différente d’un package dépendant que ce qui est déjà installé. Les dépendances de package sont indiquées dans un fichier de DESCRIPTION incorporé dans le package, mais sont parfois incomplets. Vous pouvez utiliser un package appelé [igraph](https://igraph.org/r/) pour articuler complètement le graphique de dépendance.

Si vous devez installer plusieurs packages ou si vous souhaitez vous assurer que tous les membres de votre organisation disposent du type de package et de la version corrects, nous vous recommandons d’utiliser le package [miniCRAN](https://mran.microsoft.com/package/miniCRAN) pour analyser la chaîne de dépendance complète. minicRAN crée un référentiel local qui peut être partagé entre plusieurs utilisateurs ou ordinateurs. Pour plus d’informations, consultez [créer un référentiel de package local à l’aide de miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="package-sources-versions-and-formats"></a>Sources, versions et formats des packages

Il existe plusieurs sources pour les packages R, tels que [cran](https://cran.r-project.org/) et [bioconductrice](https://www.bioconductor.org/). Le site officiel de la langue R (<https://www.r-project.org/>) répertorie un grand nombre de ces ressources. Microsoft offre [MRAN](https://mran.microsoft.com/) pour sa distribution de R ([MRO](https://mran.microsoft.com/open)) Open source et d’autres packages. De nombreux packages sont publiés sur GitHub, où les développeurs peuvent obtenir le code source.

::: moniker range=">=sql-server-2016||=sqlallproducts-allversions"
Les packages R s’exécutent sur plusieurs plateformes informatiques. Assurez-vous que les versions que vous installez sont des binaires Windows.
::: moniker-end

::: moniker range=">=sql-server-linux-ver15||=sqlallproducts-allversions"
Les packages R s’exécutent sur plusieurs plateformes informatiques. Assurez-vous que les versions que vous installez sont des binaires Linux.
::: moniker-end

### <a name="know-which-library-youre-installing-to-and-which-packages-are-already-installed"></a>Connaître la bibliothèque sur laquelle vous effectuez l’installation et les packages déjà installés

Si vous avez déjà modifié l’environnement r sur l’ordinateur, avant d’installer quoi que ce soit, assurez-vous que la variable `.libPath` d’environnement r n’utilise qu’un seul chemin d’accès.

Ce chemin d’accès doit pointer vers le dossier R_SERVICES de l’instance. Pour plus d’informations, notamment sur la manière de déterminer quels packages sont déjà installés, consultez [obtenir des informations sur](../package-management/r-package-information.md)les packages R.

## <a name="if-youre-new-to-sql-server"></a>Si vous ne connaissez pas SQL Server

En tant que développeur R travaillant sur du code s’exécutant sur SQL Server, les stratégies de sécurité protégeant le serveur contraignent votre capacité à contrôler l’environnement R. Les conseils suivants décrivent des situations typiques et fournissent des suggestions pour travailler dans cet environnement.

### <a name="r-user-libraries-not-supported-on-sql-server"></a>Bibliothèques utilisateur R: non prises en charge sur SQL Server

Les développeurs r qui doivent installer de nouveaux packages R sont habitués à installer des packages à l’adresse, à l’aide d’une bibliothèque utilisateur privée, chaque fois que la bibliothèque par défaut n’est pas disponible, ou lorsque le développeur n’est pas un administrateur sur l’ordinateur. Par exemple, dans un environnement de développement r type, l’utilisateur doit ajouter l’emplacement du package à la variable `libPath`d’environnement r, ou référencer le chemin d’accès complet du package, comme suit:

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Cela ne fonctionne pas lors de l’exécution de solutions R dans SQL Server, car les packages R doivent être installés dans une bibliothèque par défaut spécifique associée à l’instance. Quand un package n’est pas disponible dans la bibliothèque par défaut, vous recevez cette erreur lorsque vous essayez d’appeler le package:

*Erreur dans la bibliothèque (xxx): il n’existe aucun package nommé’package-name'*

Pour plus d’informations sur la façon d’installer des packages R dans SQL Server, consultez [installer de nouveaux packages r sur SQL Server machine learning services ou SQL Server R services](install-additional-r-packages-on-sql-server.md).

### <a name="how-to-avoid-package-not-found-errors"></a>Comment éviter les erreurs «package introuvable»

L’utilisation des instructions suivantes vous aidera à éviter les erreurs «package introuvable».

+ Éliminez les dépendances sur les bibliothèques utilisateur.

    Il s’agit d’une pratique de développement incorrecte pour installer les packages R requis dans une bibliothèque utilisateur personnalisée. Cela peut entraîner des erreurs si une solution est exécutée par un autre utilisateur qui n’a pas accès à l’emplacement de la bibliothèque.

    En outre, si un package est installé dans la bibliothèque par défaut, le runtime R charge le package à partir de la bibliothèque par défaut, même si vous spécifiez une version différente dans le code R.

+ Assurez-vous que votre code est en mesure de s’exécuter dans un environnement partagé.

+ Évitez d’installer des packages dans le cadre d’une solution. Si vous n’avez pas les autorisations nécessaires pour installer des packages, le code échoue. Même si vous disposez des autorisations nécessaires pour installer des packages, vous devez le faire séparément du code que vous souhaitez exécuter.

+ Vérifiez votre code pour vous assurer qu’il ne contient pas d’appel à des packages désinstallés.

+ Mettez à jour votre code pour supprimer les références directes aux chemins d’accès des packages R ou des bibliothèques R.

+ Identifiez la bibliothèque de packages associée à l’instance. Pour plus d’informations, consultez [obtenir des informations sur les packages R](../package-management/r-package-information.md).

## <a name="see-also"></a>Voir aussi

+ [Installer de nouveaux packages R](install-additional-r-packages-on-sql-server.md)
+ [Installer de nouveaux packages Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Didacticiels, exemples, solutions](../tutorials/machine-learning-services-tutorials.md)