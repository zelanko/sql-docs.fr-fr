---
title: Spécification d’un test de nœud dans le chemin d’accès d’emplacement (SQLXML)
description: Découvrez comment spécifier un test de nœud dans le chemin d’accès d’emplacement d’une requête XPath SQLXML 4,0.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e0b7934b73589f71e5152bff33b2080c6eeb353e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85649746"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Spécification d'un test de nœud dans le chemin d'accès d'emplacement (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Un test de nœud spécifie le type de nœud sélectionné par le niveau d'emplacement. Chaque axe (**enfant**, **parent**, **attribut**ou **Self**) a un type de nœud principal. Pour l’axe **attribute** , le type de nœud principal est **\<attribute>** . Pour les axes **parent**, **enfant**et **Self** , le type de nœud principal est **\<element>** .  
  
> [!NOTE]  
>  Le test de nœud générique * (par exemple, `child::*`) n'est pas pris en charge.  
  
## <a name="node-test-example-1"></a>Test de nœud : exemple 1  
 Le chemin d’accès de l’emplacement `child::Customer` sélectionne **\<Customer>** les éléments enfants du nœud de contexte.  
  
 Dans cet exemple, `child` est l'axe et `Customer` est le test de nœud. Le type de nœud principal de l’axe **enfant** est **\<element>** . Par conséquent, le test de nœud a la valeur TRUE si le **\<Customer>** nœud est un **\<element>** nœud. Si le nœud de contexte n’a pas **\<Customer>** d’enfants, un ensemble de nœuds vide est retourné.  
  
## <a name="node-test-example-2"></a>Test de nœud : exemple 2  
 Le chemin d’accès de l’emplacement `attribute::CustomerID` sélectionne l’attribut **CustomerID** du nœud de contexte.  
  
 Dans l’exemple, `attribute` est l’axe et `CustomerID` est le test de nœud. Le type de nœud principal de l’axe d' **attribut** est **\<attribute>** . Par conséquent, le test de nœud a la valeur TRUE si **CustomerID** est un **\<attribute>** nœud. Si le nœud de contexte n’a pas de **CustomerID**, un ensemble de nœuds vide est retourné.  
  
> [!NOTE]  
>  Dans cette implémentation de XPath, si une étape de localisation fait référence à un **\<element>** ou à un **\<attribute>** type qui n’est pas déclaré dans le schéma, une erreur est générée. Dans une implémentation de XPath dans MSXML, un ensemble de nœud vide est renvoyé.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Syntaxe abrégée des axes  
 La syntaxe abrégée suivante est prise en charge pour le chemin d'accès d'emplacement :  
  
-   `attribute::` peut être abrégé en `@`.  
  
     Le chemin d'accès d'emplacement `Customer[@CustomerID="ALFKI"]` est identique à `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` peut être omis dans un niveau d'emplacement.  
  
     Par conséquent, **Child** est l’axe par défaut. Le chemin d'accès d'emplacement `Customer/Order` est identique à `child::Customer/child::Order`.  
  
-   `self::node()` peut être abrégé en un point et `parent::node()` peut être abrégé en deux points (..).  
  
  
