---
title: "Packages installés dans les bibliothèques utilisateur | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99ffd9b8-aa6d-4ac2-9840-4e66d0463978
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b4d5c7f3d1d0da5e1967140fcbdfcf60ba4571e7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="packages-installed-in-user-libraries"></a>Packages installés dans les bibliothèques utilisateur

Un utilisateur non administrateur ne peut pas installer un nouveau package R à l’emplacement par défaut, car les packages sont installés par défaut dans une bibliothèque utilisateur privée. 

Dans un environnement de développement R standard, pour référencer le package dans le code, l’utilisateur pourrait ajouter l’emplacement à la variable d’environnement R `libPath`, ou référencer le chemin d’accès complet du package, comme ceci :  
  
~~~~
library("c:/Users/<username>/R/win-library/packagename")  
~~~~

## <a name="problems-with-packages-in-user-libraries"></a>Problèmes avec les packages dans les bibliothèques utilisateur

Toutefois, dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], cette solution de contournement n’est **pas** possible, et les packages doivent être installés dans la bibliothèque par défaut. Sinon, vous risquez d’obtenir ce type d’erreur quand vous essayez d’appeler le package :

*Erreur dans library(xxx) : package « xxx » introuvable*
 

Quand vous migrez des solutions R à exécuter dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], il est important d’effectuer les opérations suivantes :
+ Installez tous les packages dont vous avez besoin dans la bibliothèque par défaut.
+ Modifiez le code pour que les packages se chargent à partir de la bibliothèque par défaut, et non à partir de répertoires ad hoc ou de bibliothèques utilisateur.
+ Vérifiez votre code pour vous assurer qu’il ne contient pas d’appel à des packages désinstallés.
+ Modifiez le code susceptible d’essayer d’installer des packages de façon dynamique.
 
Si un package est installé dans la bibliothèque par défaut, le runtime R charge ce package à partir de la bibliothèque par défaut, même si une autre bibliothèque est spécifiée dans le code R.

## <a name="see-also"></a>Voir aussi
