---
title: Marqueurs de paramètres Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- parameter markers [ODBC]
ms.assetid: 07213d04-cd31-45fd-a8c8-2e16e09eeaf4
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: 132473de586094f79dd34c999d44f6dd59aefaef
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303570"
---
# <a name="parameter-markers"></a>Marqueurs de paramètres
Conformément aux spécifications SQL-92, une application ne peut pas placer de marqueurs de paramètres aux endroits suivants. Pour une liste plus complète, consultez les spécifications SQL-92.  
  
-   Dans une liste **SELECT**  
  
-   Comme les deux *expressions* dans une *comparaison-prédicate*  
  
-   En tant qu’opérands d’un opérateur binaire  
  
-   En tant que premier et deuxième opérands d’une opération **BETWEEN**  
  
-   En tant que premier et troisième opérands d’une opération **BETWEEN**  
  
-   Comme l’expression et la première valeur d’une opération **IN**  
  
-   En tant qu’opéra d’une opération non ordonnée ou  
  
-   Comme argument d’un *set-fonction-référence*  
  
 Pour de plus amples renseignements sur les marqueurs de paramètres, consultez les spécifications SQL-92. Pour plus d’informations sur les paramètres, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).
