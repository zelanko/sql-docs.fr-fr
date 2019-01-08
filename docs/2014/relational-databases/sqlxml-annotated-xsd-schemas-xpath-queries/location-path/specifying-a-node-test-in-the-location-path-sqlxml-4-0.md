---
title: Spécification d’un Test de nœud dans le chemin d’accès d’emplacement (SQLXML 4.0) | Microsoft Docs
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7450810f45d81dd1530699677a80a052840ed867
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806001"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Spécification d'un test de nœud dans le chemin d'accès d'emplacement (SQLXML 4.0)
  Un test de nœud spécifie le type de nœud sélectionné par le niveau d'emplacement. Chaque axe (`child`, `parent`, `attribute` ou `self`) possède un type de nœud principal. Pour le `attribute` axe, le type de nœud principal est  **\<attribut >**. Pour le `parent`, `child`, et `self` axes, le type de nœud principal est  **\<élément >**.  
  
> [!NOTE]  
>  Le test de nœud générique * (par exemple, `child::*`) n'est pas pris en charge.  
  
## <a name="node-test-example-1"></a>Test de nœud : Exemple 1  
 Le chemin d’accès de l’emplacement `child::Customer` sélectionne  **\<client >** éléments enfants du nœud de contexte.  
  
 Dans cet exemple, `child` est l'axe et `Customer` est le test de nœud. Le type de nœud principal pour le `child` axe est  **\<élément >**. Par conséquent, le test de nœud est TRUE si le  **\<client >** nœud est un  **\<élément >** nœud. Si le nœud de contexte n’a pas  **\<client >** enfants, un ensemble de nœuds vide est retourné.  
  
## <a name="node-test-example-2"></a>Test de nœud : Exemple 2  
 Le chemin d’accès de l’emplacement `attribute::CustomerID` sélectionne le **CustomerID** attribut du nœud de contexte.  
  
 Dans l’exemple, `attribute` est l’axe et `CustomerID` est le test de nœud. Le type de nœud principal de le `attribute` axe est  **\<attribut >**. Par conséquent, le test de nœud est TRUE si **CustomerID** est un  **\<attribut >** nœud. Si le nœud de contexte n’a pas **CustomerID**, un ensemble de nœuds vide est retourné.  
  
> [!NOTE]  
>  Dans cette implémentation de XPath, si une étape de localisation fait référence à un  **\<élément >** ou un  **\<attribut >** type qui n’est pas déclaré dans le schéma, une erreur est générée. Dans une implémentation de XPath dans MSXML, un ensemble de nœud vide est renvoyé.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Syntaxe abrégée des axes  
 La syntaxe abrégée suivante est prise en charge pour le chemin d'accès d'emplacement :  
  
-   `attribute::` peut être abrégé en `@`.  
  
     Le chemin d'accès d'emplacement `Customer[@CustomerID="ALFKI"]` est identique à `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` peut être omis dans un niveau d'emplacement.  
  
     Par conséquent, `child` est l'axe par défaut. Le chemin d'accès d'emplacement `Customer/Order` est identique à `child::Customer/child::Order`.  
  
-   `self::node()` peut être abrégé en un point et `parent::node()` peut être abrégé en deux points (..).  
  
  
