---
title: "Types de données C par défaut | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83040ffdab8b9715fc8caeb024bec6a9fc05d4d4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="default-c-data-types"></a>Types de données C par défaut
Si une application spécifie SQL_C_DEFAULT dans **SQLBindCol**, **SQLGetData**, ou **SQLBindParameter**, le pilote part du principe que le type de données C de la sortie ou la mémoire tampon d’entrée correspond au type de données SQL de la colonne ou du paramètre auquel est liée la mémoire tampon.  
  
> [!IMPORTANT]  
>  Applications interopérables ne doivent pas utiliser SQL_C_DEFAULT. Au lieu de cela, ils doivent toujours spécifier le type C de la mémoire tampon qu’ils utilisent. Il s’agit, car les pilotes ne peut pas déterminer toujours correctement le type C par défaut, pour les raisons suivantes :  
  
-   Si le SGBD promeut un type de données SQL d’une colonne ou un paramètre, le pilote ne peut pas déterminer le type de données SQL d’origine d’une colonne ou un paramètre. Par conséquent, il ne peut pas déterminer le type de données C par défaut.  
  
-   Si le pilote ne peut pas déterminer si une colonne particulière ou un paramètre est signé, comme c’est souvent le cas lorsque cela est géré par le SGBD, le pilote ne peut pas déterminer si le type données C par défaut correspondantes doit être signé ou non signé.  
  
     Étant donné que SQL_C_DEFAULT est fourni uniquement comme une facilité de programmation, l’application ne perd pas toutes les fonctionnalités lorsqu’il spécifie le type de données C réel.  
  
 Un tableau indiquant le type de données C par défaut pour chaque type de données SQL est inclus dans [conversion des données à partir de SQL pour Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md), plus loin dans cette annexe.

