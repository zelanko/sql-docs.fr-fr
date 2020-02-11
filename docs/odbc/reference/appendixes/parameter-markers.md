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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100580"
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
