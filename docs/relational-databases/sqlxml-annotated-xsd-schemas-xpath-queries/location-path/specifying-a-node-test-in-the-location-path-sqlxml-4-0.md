---
title: "Spécification d’un Test de nœud dans le chemin d’accès d’emplacement (SQLXML 4.0) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 026cc54ab05fa07dca6a668902e286d9903dd94c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Spécification d'un test de nœud dans le chemin d'accès d'emplacement (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Un test de nœud Spécifie le type de nœud sélectionné par l’étape de localisation. Chaque axe (**enfant**, **parent**, **attribut**, ou **self**) a un type de nœud principal. Pour le **attribut** axe, le type de nœud principal est  **\<attribut >**. Pour le **parent**, **enfant**, et **self** axes, le type de nœud principal est  **\<élément >**.  
  
> [!NOTE]  
>  Le test de nœud générique * (par exemple, `child::*`) n'est pas pris en charge.  
  
## <a name="node-test-example-1"></a>Test de nœud : Exemple 1  
 Le chemin d’accès d’emplacement `child::Customer` sélectionne  **\<client >** éléments enfants du nœud de contexte.  
  
 Dans cet exemple, `child` est l'axe et `Customer` est le test de nœud. Le type de nœud principal pour le **enfant** axe est  **\<élément >**. Par conséquent, le test de nœud a la valeur TRUE si le  **\<client >** le nœud est un  **\<élément >** nœud. Si le nœud de contexte n’a pas  **\<client >** enfants, un ensemble de nœuds vide est retourné.  
  
## <a name="node-test-example-2"></a>Test de nœud : exemple 2  
 Le chemin d’accès d’emplacement `attribute::CustomerID` sélectionne le **CustomerID** attribut du nœud de contexte.  
  
 Dans l’exemple, `attribute` est l’axe et `CustomerID` est le test de nœud. Le type de nœud principal de la **attribut** axe est  **\<attribut >**. Par conséquent, le test de nœud a la valeur TRUE si **CustomerID** est un  **\<attribut >** nœud. Si le nœud de contexte n’a pas **CustomerID**, un ensemble de nœuds vide est retourné.  
  
> [!NOTE]  
>  Dans cette implémentation de XPath, si une étape d’emplacement fait référence à un  **\<élément >** ou  **\<attribut >** type qui n’est pas déclaré dans le schéma, une erreur est générée. Dans une implémentation de XPath dans MSXML, un ensemble de nœud vide est renvoyé.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Syntaxe abrégée des axes  
 La syntaxe abrégée suivante est prise en charge pour le chemin d'accès d'emplacement :  
  
-   `attribute::` peut être abrégé en `@`.  
  
     Le chemin d'accès d'emplacement `Customer[@CustomerID="ALFKI"]` est identique à `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` peut être omis dans un niveau d'emplacement.  
  
     Par conséquent, **enfant** est l’axe par défaut. Le chemin d'accès d'emplacement `Customer/Order` est identique à `child::Customer/child::Order`.  
  
-   `self::node()` peut être abrégé en un point et `parent::node()` peut être abrégé en deux points (..).  
  
  
