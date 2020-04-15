---
title: Déclarer la version ODBC de l’application&#39;(en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: ba346ed7f7a261446110c5513026d20a86fd3a19
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285229"
---
# <a name="declaring-the-application39s-odbc-version"></a>Déclarer la version ODBC de l’application&#39;
Avant qu’une application n’attribue une connexion, elle doit définir l’attribut SQL_ATTR_ODBC_VERSION environnement. Cet attribut indique que l’application suit les spécifications ODBC *2.x* ou ODBC *3.x* lors de l’utilisation des éléments suivants :  
  
-   **SQLSTATES**. De nombreuses valeurs SQLSTATE sont différentes dans ODBC *2.x* et ODBC *3.x*.  
  
-   **Identifiants de date, d’heure et de type Timestamp**. Le tableau suivant affiche les identificateurs de type pour les données de date, d’heure et d’humidité du temps dans ODBC *2.x* et ODBC *3.x*.  
  
    |ODBC *2.x*|ODBC *3.x*|  
    |----------------|----------------|  
    |**Identificateurs de types SQL**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**Identifiants de type C**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_  **Argument dans SQLTables**. Dans ODBC *2.x*, les caractères wildcard ("%" et "") dans l’argument *CatalogName* sont traités littéralement. Dans ODBC *3.x*, ils sont traités comme des personnages wildcard. Ainsi, une application qui suit les spécifications ODBC *2.x* ne peut pas les utiliser comme caractères wildcard et ne leur échappe pas lors de leur utilisation comme littérals. Une application qui suit les spécifications ODBC *3.x* peut les utiliser comme caractères wildcard ou y échapper et les utiliser comme littérals. Pour plus d’informations, voir [Arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Les pilotes ODBC *3.x* Driver Manager et ODBC *3.x* vérifient la version des spécifications ODBC auxquelles une application est écrite et répondent en conséquence. Par exemple, si l’application suit les spécifications ODBC *2.x* et appelle **SQLExecute** avant d’appeler **SQLPrepare**, l’ODBC *3.x* Driver Manager renvoie SQLSTATE S1010 (erreur de séquence de fonction). Si l’application suit les spécifications ODBC *3.x,* le gestionnaire de conducteur renvoie SQLSTATE HY010 (erreur de séquence de fonction). Pour plus d’informations, voir [Compatibilité vers l’arrière et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Les applications qui suivent les spécifications ODBC *3.x* doivent utiliser le code conditionnel pour éviter d’utiliser des fonctionnalités nouvelles à ODBC *3.x* lorsque vous travaillez avec les pilotes ODBC *2.x.* Les pilotes ODBC *2.x* ne prennent pas en charge les fonctionnalités nouvelles à ODBC *3.x* juste parce que l’application déclare qu’elle suit la spécification ODBC *3.x.* En outre, les pilotes ODBC *3.x* ne cessent de prendre en charge les fonctionnalités nouvelles à ODBC *3.x* juste parce que l’application déclare qu’elle suit la spécification ODBC *2.x.*
