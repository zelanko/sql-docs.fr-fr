---
title: "Déclaration de l’Application &#39; s ODBC Version | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a58aebc6517268c054a4d2ac92066eb0d0469d2c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="declaring-the-application39s-odbc-version"></a>Déclaration de l’Application &#39; s Version ODBC
Une application alloue une connexion, il doit au préalable l’attribut d’environnement SQL_ATTR_ODBC_VERSION. Cet attribut indique que l’application suit ODBC 2. *x* ou ODBC 3. *x* spécification lorsque vous utilisez les éléments suivants :  
  
-   **SQLSTATE**. Nombre de valeurs SQLSTATE est différent dans ODBC 2. *x* et ODBC 3. *x*.  
  
-   **Date, Time et Timestamp, Type identificateurs**. Le tableau suivant présente les identificateurs de type de date et d’heure données timestamp ODBC 2. *x* et ODBC 3. *x*.  
  
    |ODBC 2. *x*|ODBC 3. *x*|  
    |----------------|----------------|  
    |**Identificateurs de types SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Identificateurs de Type C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   *Nom de catalogue***Argument dans SQLTables**. Dans ODBC 2. *x*, les caractères génériques (« % » et « _ ») dans le *CatalogName* argument sont traités de manière littérale. Dans ODBC 3. *x*, elles sont traitées comme des caractères génériques. Par conséquent, une application qui suit ODBC 2. *x* spécification ne peut pas utiliser ces caractères génériques caractères et n’échappe pas les lors de leur utilisation en tant que littéraux. Une application qui suit la ODBC 3. *x* spécification peut les utiliser en tant que caractères génériques ou échappement et les utiliser en tant que littéraux. Pour plus d’informations, consultez [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 La version 3 ODBC*.x* du Gestionnaire de pilotes alors que ODBC 3*.x* pilotes vérifier la version de la spécification ODBC dans lequel une application est écrite et réagir en conséquence. Par exemple, si l’application suit ODBC 2. *x* spécification et appelle **SQLExecute** avant d’appeler **SQLPrepare**, la version 3 ODBC*.x* du Gestionnaire de pilotes retourne SQLSTATE S1010 (erreur de séquence de fonction). Si l’application suit les ODBC 3*.x* spécification, le Gestionnaire de pilotes retourne SQLSTATE HY010 (erreur de séquence de fonction). Pour plus d’informations, consultez [la compatibilité descendante et la conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Applications qui suivent l’ODBC 3. *x* spécification doit utiliser le code conditionnel pour éviter d’utiliser la fonctionnalité nouvelle ODBC 3. *x* lorsque vous travaillez avec ODBC 2. *x* pilotes. ODBC 2. *x* pilotes ne prennent pas en charge les fonctionnalités nouvelles ODBC 3. *x* parce que l’application déclare qu’il suit la ODBC 3. *x* spécification. En outre, ODBC 3. *x* pilotes cesse pas en charge des fonctionnalités nouvelles ODBC 3. *x* parce que l’application déclare qu’il suit ODBC 2. *x* spécification.
