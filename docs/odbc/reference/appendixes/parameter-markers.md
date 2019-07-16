---
title: Marqueurs de paramètres | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.openlocfilehash: acb8d5f9687798bc0efa514ee8646b16140fcd36
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100580"
---
# <a name="parameter-markers"></a>Marqueurs de paramètres
Conformément à la spécification SQL-92, une application ne peut pas placer des marqueurs de paramètres dans les emplacements suivants. Pour une liste plus complète, consultez la spécification de SQL-92.  
  
-   Dans un **sélectionnez** liste  
  
-   À la fois comme *expressions* dans un *prédicat de comparaison*  
  
-   En tant que les deux opérandes d’un opérateur binaire  
  
-   En tant que les deux les premier et deuxième opérandes d’un **BETWEEN** opération  
  
-   Comme le premier et le troisième opérandes d’un **BETWEEN** opération  
  
-   En tant que l’expression et la première valeur d’un **IN** opération  
  
-   Comme opérande d’un opérateur unaire + ou - opération  
  
-   Comme l’argument d’un *référence de jeu (fonction)*  
  
 Pour plus d’informations sur les marqueurs de paramètres, consultez la spécification de SQL-92. Pour plus d’informations sur les paramètres, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).
