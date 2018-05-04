---
title: Types de données C par défaut | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70964b9d2a438805194f9816473fdf81d0d39f3f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="default-c-data-types"></a>Types de données C par défaut
Si une application spécifie SQL_C_DEFAULT dans **SQLBindCol**, **SQLGetData**, ou **SQLBindParameter**, le pilote part du principe que le type de données C de la sortie ou la mémoire tampon d’entrée correspond au type de données SQL de la colonne ou du paramètre auquel est liée la mémoire tampon.  
  
> [!IMPORTANT]  
>  Applications interopérables ne doivent pas utiliser SQL_C_DEFAULT. Au lieu de cela, ils doivent toujours spécifier le type C de la mémoire tampon qu’ils utilisent. Il s’agit, car les pilotes ne peut pas déterminer toujours correctement le type C par défaut, pour les raisons suivantes :  
  
-   Si le SGBD promeut un type de données SQL d’une colonne ou un paramètre, le pilote ne peut pas déterminer le type de données SQL d’origine d’une colonne ou un paramètre. Par conséquent, il ne peut pas déterminer le type de données C par défaut.  
  
-   Si le pilote ne peut pas déterminer si une colonne particulière ou un paramètre est signé, comme c’est souvent le cas lorsque cela est géré par le SGBD, le pilote ne peut pas déterminer si le type données C par défaut correspondantes doit être signé ou non signé.  
  
     Étant donné que SQL_C_DEFAULT est fourni uniquement comme une facilité de programmation, l’application ne perd pas toutes les fonctionnalités lorsqu’il spécifie le type de données C réel.  
  
 Un tableau indiquant le type de données C par défaut pour chaque type de données SQL est inclus dans [conversion des données à partir de SQL pour Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md), plus loin dans cette annexe.
