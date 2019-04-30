---
title: Déclaration de l’Application&#39;s ODBC Version | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c5bb124af74d1fa009a61237edb54a9c8baec74
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267691"
---
# <a name="declaring-the-application39s-odbc-version"></a>Déclaration de l’Application&#39;s Version ODBC
Une application alloue une connexion, il doit au préalable l’attribut d’environnement SQL_ATTR_ODBC_VERSION. Cet attribut indique que l’application suit ODBC 2. *x* ou ODBC 3. *x* spécification lors de l’utilisation des éléments suivants :  
  
-   **SQLSTATEs**. Nombre de valeurs SQLSTATE est différente dans ODBC 2. *x* et ODBC 3. *x*.  
  
-   **Date, Time et identificateurs de Type Timestamp**. Le tableau suivant présente les identificateurs de type pour la date, time et timestamp des données dans ODBC 2. *x* et ODBC 3. *x*.  
  
    |ODBC 2.*x*|ODBC 3.*x*|  
    |----------------|----------------|  
    |**Identificateurs de types SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Identificateurs de Type C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_  **Argument dans SQLTables**. Dans ODBC 2. *x*, les caractères génériques (« % » et « _ ») dans le *CatalogName* argument sont traités de manière littérale. Dans ODBC 3. *x*, ils sont traités comme des caractères génériques. Par conséquent, une application qui suit ODBC 2. *x* spécification ne peut pas utiliser ces caractères génériques caractères et n’échappe pas à les lors de leur utilisation en tant que littéraux. Une application qui suit la ODBC 3. *x* spécification peut les utiliser en tant que caractères génériques ou échappement et les utiliser en tant que littéraux. Pour plus d’informations, consultez [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Le 3 ODBC *.x* Gestionnaire de pilotes alors que ODBC 3 *.x* pilotes vérifier la version de la spécification ODBC dans lequel une application est écrite et réagir en conséquence. Par exemple, si l’application suit ODBC 2. *x* spécification et appelle **SQLExecute** avant d’appeler **SQLPrepare**, les 3 ODBC *.x* Gestionnaire de pilotes retourne SQLSTATE S1010 () Erreur de séquence de fonction). Si l’application suit la ODBC 3 *.x* spécification, le Gestionnaire de pilotes retourne SQLSTATE HY010 (erreur de séquence de fonction). Pour plus d’informations, consultez [la compatibilité descendante et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Applications qui suivent l’ODBC 3. *x* spécification doit utiliser le code conditionnel pour éviter d’utiliser les fonctionnalités nouvelles pour ODBC 3. *x* lorsque vous travaillez avec ODBC 2. *x* pilotes. ODBC 2. *x* pilotes ne gèrent pas les fonctionnalités nouvelles pour ODBC 3. *x* simplement parce que l’application déclare qu’il suit le ODBC 3. *x* spécification. En outre, ODBC 3. *x* pilotes cesse pas prendre en charge des fonctionnalités nouvelles pour ODBC 3. *x* simplement parce que l’application déclare qu’il suit ODBC 2. *x* spécification.
