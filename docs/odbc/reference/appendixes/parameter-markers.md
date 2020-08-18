---
description: Marqueurs de paramètres
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
author: David-Engel
ms.author: v-daenge
ms.reviewer: ''
ms.openlocfilehash: a585fb983a8f1662cdd42d361f106a76bfd47cb6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483232"
---
# <a name="parameter-markers"></a>Marqueurs de paramètres
Conformément à la spécification SQL-92, une application ne peut pas placer de marqueurs de paramètres aux emplacements suivants. Pour obtenir une liste plus complète, consultez la spécification SQL-92.  
  
-   Dans une liste de **sélection**  
  
-   À la fois en tant qu' *expressions* dans un *prédicat de comparaison*  
  
-   Comme opérandes d’un opérateur binaire  
  
-   En tant que premier et deuxième opérandes d’une opération **between**  
  
-   Comme les premier et troisième opérandes d’une opération **between**  
  
-   À la fois l’expression et la première valeur d’une opération **in**  
  
-   Comme opérande d’une opération + or unaire  
  
-   En tant qu’argument d’une *fonction Set-Function-Reference*  
  
 Pour plus d’informations sur les marqueurs de paramètres, consultez la spécification SQL-92. Pour plus d’informations sur les paramètres, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).
