---
title: "Comment éviter les erreurs sur les packages R sont installés dans les bibliothèques utilisateur | Documents Microsoft"
titleSuffix: SQL Server
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99ffd9b8-aa6d-4ac2-9840-4e66d0463978
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: b7f640cc33cb61ab8dffc57edb3b522808129880
ms.sourcegitcommit: c08d665754f274e6a85bb385adf135c9eec702eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="avoiding-errors-on-r-packages-installed-in-user-libraries"></a>Comment éviter les erreurs sur les packages R sont installés dans les bibliothèques utilisateur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Les utilisateurs expérimentés de R sont habitués à l’installation des packages R dans une bibliothèque de l’utilisateur, chaque fois que la bibliothèque par défaut est bloqué ou non disponible. Toutefois, cette approche n’est pas pris en charge dans SQL Server, et l’installation dans une bibliothèque de l’utilisateur se termine généralement une erreur « package introuvable ».

Cet article décrit les solutions de contournement pour vous aider à éviter cette erreur. Il explique comment vous pouvez modifier votre code R et suggère le processus d’installation de package R correct pour l’utilisation de packages R à partir d’une instance de SQL Server.

## <a name="why-r-user-libraries-cannot-be-accessed-from-sql-server"></a>Pourquoi les bibliothèques d’utilisateur R ne sont pas accessibles à partir de SQL Server

Les développeurs R qui ont besoin d’installer de nouveaux packages R sont habitués à l’installation des packages à volonté, à l’aide d’un privés, la bibliothèque de l’utilisateur chaque fois que la bibliothèque par défaut n’est pas disponible, ou lorsque le développeur n’est pas un administrateur sur l’ordinateur.

Par exemple, dans un environnement de développement R classique, l’utilisateur devez ajouter l’emplacement du package à la variable d’environnement R `libPath`, ou référence le chemin d’accès complet du package, comme suit :

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Cela ne fonctionne pas lors de l’exécution des solutions R dans SQL Server, car les packages R doivent être installés dans une bibliothèque spécifique par défaut qui est associée à l’instance. Lorsqu’un package n’est pas disponible dans la bibliothèque par défaut, vous obtenez cette erreur lorsque vous essayez d’appeler le package :

*Erreur dans library(xxx) : il n’existe aucun package appelé 'package-name'*

## <a name="how-to-avoid-package-not-found-errors"></a>Comment éviter les erreurs de « package introuvable »

+ Éliminer les dépendances sur les bibliothèques utilisateur 

    Il est pratique de développement incorrecte pour installer les packages R requis dans une bibliothèque d’utilisateur personnalisée, comme il peut entraîner des erreurs si une solution est exécutée par un autre utilisateur qui n’a pas accès à l’emplacement de la bibliothèque.

    En outre, si un package est installé dans la bibliothèque par défaut, le runtime R charge le package à partir de la bibliothèque par défaut, même si vous avez spécifié une version différente dans le code R.

+ Modifiez votre code s’exécute dans un environnement partagé.

+ Évitez d’installer des packages dans le cadre d’une solution. Si vous n’êtes pas autorisé à installer des packages, le code échoue. Même si vous avez les autorisations nécessaires pour installer des packages, vous devez procéder séparément du reste du code que vous souhaitez exécuter.

+ Vérifiez votre code pour vous assurer qu’il ne contient pas d’appel à des packages désinstallés.

+ Mettre à jour votre code pour supprimer des références directes aux chemins des packages R ou des bibliothèques R. 

+ Ignore la bibliothèque de package est associée à l’instance. Pour plus d’informations, consultez [packages R sont installés avec SQL Server](installing-and-managing-r-packages.md)
