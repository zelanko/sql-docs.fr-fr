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
ms.openlocfilehash: ea97e3cd7a8fee3b3397524bf2c48c428d6a0be0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076839"
---
# <a name="declaring-the-application39s-odbc-version"></a>Déclaration de l’Application&#39;s Version ODBC
Une application alloue une connexion, il doit au préalable l’attribut d’environnement SQL_ATTR_ODBC_VERSION. Cet attribut indique que l’application suit ODBC *2.x* ou ODBC *3.x* spécification lors de l’utilisation des éléments suivants :  
  
-   **SQLSTATEs**. Nombre de valeurs SQLSTATE est différente dans ODBC *2.x* et ODBC *3.x*.  
  
-   **Date, Time et identificateurs de Type Timestamp**. Le tableau suivant présente les identificateurs de type de données date, time et timestamp dans ODBC *2.x* et ODBC *3.x*.  
  
    |ODBC *2.x*|ODBC *3.x*|  
    |----------------|----------------|  
    |**Identificateurs de types SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Identificateurs de Type C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_  **Argument dans SQLTables**. Dans ODBC *2.x*, les caractères génériques (« % » et « _ ») dans le *CatalogName* argument sont traités de manière littérale. Dans ODBC *3.x*, ils sont traités comme des caractères génériques. Par conséquent, une application qui suit ODBC *2.x* spécification ne peut pas utiliser ces caractères génériques caractères et n’échappe pas à les lors de leur utilisation en tant que littéraux. Une application qui suit ODBC *3.x* spécification peut les utiliser en tant que caractères génériques ou échappement et les utiliser en tant que littéraux. Pour plus d’informations, consultez [Arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 ODBC *3.x* Gestionnaire de pilotes et ODBC *3.x* pilotes vérifier la version de la spécification ODBC dans lequel une application est écrite et réagir en conséquence. Par exemple, si l’application suit ODBC *2.x* spécification et appelle **SQLExecute** avant d’appeler **SQLPrepare**, ODBC *3.x*Gestionnaire de pilotes retourne SQLSTATE S1010 (erreur de séquence de fonction). Si l’application suit ODBC *3.x* spécification, le Gestionnaire de pilotes retourne SQLSTATE HY010 (erreur de séquence de fonction). Pour plus d’informations, consultez [la compatibilité descendante et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Les applications qui suivent ODBC *3.x* spécification doit utiliser le code conditionnel pour éviter d’utiliser la fonctionnalité nouvelle vers ODBC *3.x* lorsque vous travaillez avec ODBC *2.x* pilotes. ODBC *2.x* pilotes ne prennent pas en charge fonctionnalité nouvelle vers ODBC *3.x* simplement parce que l’application déclare qu’il suit ODBC *3.x* spécification. En outre, ODBC *3.x* pilotes cesse pas prendre en charge des fonctionnalités nouvelles pour ODBC *3.x* simplement parce que l’application déclare qu’il suit ODBC *2.x* spécification.
