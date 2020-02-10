---
title: Spécification d’un test de nœud dans le chemin d’accès d’emplacement (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 1d0a3dd41259bcbf2567d34a86527865de011faf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012664"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Spécification d'un test de nœud dans le chemin d'accès d'emplacement (SQLXML 4.0)
  Un test de nœud spécifie le type de nœud sélectionné par le niveau d'emplacement. Chaque axe (`child`, `parent`, `attribute` ou `self`) possède un type de nœud principal. Pour l' `attribute` axe, le type de nœud principal est ** \<attribute>**. Pour les `parent`axes `child`, et `self` , le type de nœud principal est ** \<l’élément>**.  
  
> [!NOTE]  
>  Le test de nœud générique * (par exemple, `child::*`) n'est pas pris en charge.  
  
## <a name="node-test-example-1"></a>Test de nœud : exemple 1  
 Le chemin d' `child::Customer` accès de l’emplacement sélectionne ** \<Customer>** élément Children du nœud de contexte.  
  
 Dans cet exemple, `child` est l'axe et `Customer` est le test de nœud. Le type de nœud principal de `child` l’axe est ** \<l’élément>**. Par conséquent, le test de nœud a la valeur true si le nœud ** \<>du client** est un nœud d' ** \<élément>** . Si le nœud de contexte n’a pas ** \<de client>** d’enfants, un ensemble de nœuds vide est retourné.  
  
## <a name="node-test-example-2"></a>Test de nœud : exemple 2  
 Le chemin d' `attribute::CustomerID` accès de l’emplacement sélectionne l’attribut **CustomerID** du nœud de contexte.  
  
 Dans l’exemple, `attribute` est l’axe et `CustomerID` est le test de nœud. Le type de nœud principal de `attribute` l’axe est ** \<l’attribut>**. Par conséquent, le test de nœud a la valeur true si **CustomerID** est un ** \<attribut>** nœud. Si le nœud de contexte n’a pas de **CustomerID**, un ensemble de nœuds vide est retourné.  
  
> [!NOTE]  
>  Dans cette implémentation de XPath, si une étape de localisation fait référence à un ** \<élément>** ou à un ** \<attribut>** type qui n’est pas déclaré dans le schéma, une erreur est générée. Dans une implémentation de XPath dans MSXML, un ensemble de nœud vide est renvoyé.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Syntaxe abrégée des axes  
 La syntaxe abrégée suivante est prise en charge pour le chemin d'accès d'emplacement :  
  
-   
  `attribute::` peut être abrégé en `@`.  
  
     Le chemin d'accès d'emplacement `Customer[@CustomerID="ALFKI"]` est identique à `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   
  `child::` peut être omis dans un niveau d'emplacement.  
  
     Par conséquent, `child` est l'axe par défaut. Le chemin d'accès d'emplacement `Customer/Order` est identique à `child::Customer/child::Order`.  
  
-   
  `self::node()` peut être abrégé en un point et `parent::node()` peut être abrégé en deux points (..).  
  
  
