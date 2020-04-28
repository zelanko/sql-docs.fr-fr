---
title: Conformité de SQL-92 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], SQL-92 compliance
- desktop database drivers [ODBC], SQL-92 compliance
- SQL-92 compliance [ODBC]
- ODBC desktop database drivers [ODBC], SQL-92 compliance
ms.assetid: 50c8c7df-df01-4f4d-ad62-d059cf29d73a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac0ae5873e545afb8fcac9dd003c984b1ed303a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300699"
---
# <a name="sql-92-compliance"></a>Conformité à SQL-92
Les pilotes de base de données de bureau ODBC et le moteur Microsoft Jet sous-jacent ne sont pas conformes à SQL-92. Ils prennent en charge de nombreuses fonctionnalités qui ont été définies dans SQL-92. Certaines fonctionnalités prises en charge dans le pilote ne sont pas prises en charge dans SQL-92. Pour plus d’informations, consultez le *Guide du programmeur Microsoft Jet moteur de base de données*. Voici les principales différences entre les deux :  
  
-   Le SQL utilisé par les pilotes de base de données de bureau prend en charge des expressions plus puissantes que celles spécifiées par SQL-92.  
  
-   Différentes règles s’appliquent au prédicat BETWEEN.  
  
-   Le SQL utilisé par les pilotes de base de données de bureau et ANSI SQL prend en charge des mots clés différents.  
  
 Les fonctionnalités SQL-92 suivantes ne sont pas prises en charge par Microsoft Jet SQL :  
  
-   Instructions de sécurité, telles que GRANT et LOCK.  
  
-   DISTINCT avec références à la fonction d’agrégation.  
  
 Les fonctionnalités suivantes sont des améliorations de SQL utilisées par les pilotes de base de données de bureau qui ne sont pas spécifiés par SQL-92 :  
  
-   Instruction de transformation qui prend en charge les requêtes d’analyse croisée.  
  
-   Fonctions d’agrégation supplémentaires (**ECARTYPE** et **VarP**).  
  
> [!NOTE]  
>  Les pilotes de base de données de bureau prennent en charge la syntaxe ANSI standard pour% (percent) et _ (trait de soulignement), et non * (astérisque) et ? (point d’interrogation).
