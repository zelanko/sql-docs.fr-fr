---
title: Types de données par défaut C (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fdb787580e1c79df805f468416ab8993a1d32a26
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307050"
---
# <a name="default-c-data-types"></a>Types de données C par défaut
Si une application spécifie SQL_C_DEFAULT dans **SQLBindCol**, **SQLGetData**, ou **SQLBindParameter**, le conducteur suppose que le type de données C du tampon de sortie ou d’entrée correspond au type de données SQL de la colonne ou du paramètre auquel le tampon est lié.  
  
> [!IMPORTANT]  
>  Les applications interopérables ne doivent pas utiliser SQL_C_DEFAULT. Au lieu de cela, ils doivent toujours spécifier le type C du tampon qu’ils utilisent. C’est parce que les conducteurs ne peuvent pas toujours déterminer correctement le type C par défaut, pour les raisons suivantes:  
  
-   Si le DBMS fait la promotion d’un type de données SQL d’une colonne ou d’un paramètre, le conducteur ne peut pas déterminer le type de données SQL d’origine d’une colonne ou d’un paramètre. Par conséquent, il ne peut pas déterminer le type de données par défaut C correspondant.  
  
-   Si le conducteur ne peut pas déterminer si une colonne ou un paramètre particulier est signé, comme c’est souvent le cas lorsque cela est traité par le DBMS, le conducteur ne peut pas déterminer si le type de données par défaut C correspondant doit être signé ou non signé.  
  
     Étant donné que SQL_C_DEFAULT n’est fourni que comme commodité de programmation, l’application ne perd aucune fonctionnalité lorsqu’elle spécifie le type de données C réel.  
  
 Un tableau montrant le type de données C par défaut pour chaque type de données SQL est inclus dans [la conversion des données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md), plus tard dans cette annexe.
