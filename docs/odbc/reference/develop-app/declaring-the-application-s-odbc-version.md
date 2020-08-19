---
description: Déclaration de la version ODBC de l’application&#39;s
title: Déclaration de la version ODBC de l’application&#39;s | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ff41a7a8b56133b0a44947980805c5b46238bad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424720"
---
# <a name="declaring-the-application39s-odbc-version"></a>Déclaration de la version ODBC de l’application&#39;s
Avant d’allouer une connexion, une application doit définir l’attribut d’environnement SQL_ATTR_ODBC_VERSION. Cet attribut indique que l’application suit la spécification ODBC *2. x* ou ODBC *3. x* lors de l’utilisation des éléments suivants :  
  
-   **Sqlstates**. De nombreuses valeurs SQLSTATE sont différentes dans ODBC *2. x* et ODBC *3. x*.  
  
-   **Identificateurs de type de date, d’heure et d’horodatage**. Le tableau suivant présente les identificateurs de type pour les données de date, d’heure et d’horodatage dans ODBC *2. x* et ODBC *3. x*.  
  
    |ODBC *2. x*|ODBC *3. x*|  
    |----------------|----------------|  
    |**Identificateurs de types SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Identificateurs de type C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   Argument _nomcatalogue_**dans SQLTables**.   Dans ODBC *2. x*, les caractères génériques (« % » et « _ ») dans l’argument *nomcatalogue* sont traités littéralement. Dans ODBC *3. x*, elles sont traitées comme des caractères génériques. Ainsi, une application qui suit la spécification ODBC *2. x* ne peut pas les utiliser en tant que caractères génériques et ne les échappe pas lorsque vous les utilisez en tant que littéraux. Une application qui suit la spécification ODBC *3. x* peut les utiliser comme caractères génériques ou les placer dans une séquence d’échappement et les utiliser en tant que littéraux. Pour plus d’informations, consultez [arguments dans les fonctions de catalogue](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Les pilotes ODBC *3. x* Driver Manager et ODBC *3. x* vérifient la version de la spécification ODBC dans laquelle une application est écrite et répondent en conséquence. Par exemple, si l’application suit la spécification ODBC *2. x* et appelle **SQLExecute** avant d’appeler **SQLPrepare**, le gestionnaire de pilotes ODBC *3. x* retourne SQLState S1010 (erreur de séquence de fonction). Si l’application suit la spécification ODBC *3. x* , le gestionnaire de pilotes retourne SQLState HY010 (erreur de séquence de fonction). Pour plus d’informations, consultez [compatibilité descendante et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Les applications qui suivent la spécification ODBC *3. x* doivent utiliser du code conditionnel pour éviter d’utiliser les fonctionnalités nouvelles dans ODBC *3. x* lors de l’utilisation de pilotes ODBC *2. x* . Les pilotes ODBC *2. x* ne prennent pas en charge les fonctionnalités nouvelles à ODBC *3. x* uniquement parce que l’application déclare qu’elles suivent la spécification ODBC *3. x* . En outre, les pilotes ODBC *3. x* ne prennent pas en charge les fonctionnalités nouvelles dans ODBC *3. x* juste parce que l’application déclare qu’elles suivent la spécification ODBC *2. x* .
