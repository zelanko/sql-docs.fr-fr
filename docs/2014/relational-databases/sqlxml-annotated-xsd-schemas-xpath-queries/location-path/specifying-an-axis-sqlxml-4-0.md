---
title: Spécification d’un axe (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: rothja
ms.author: jroth
ms.openlocfilehash: 651b7899e104fe5a7dbc6d584ceba6e5cf8de570
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055120"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Spécification d'un axe (SQLXML 4.0)
    
-   L'axe spécifie la relation d'arborescence entre les nœuds sélectionnés par l'étape d'emplacement et le nœud de contexte. Les axes suivants sont admis :`child`  
  
     Contient l'enfant du nœud du contexte.  
  
     L’expression XPath suivante (chemin d’accès d’emplacement) sélectionne à partir du nœud de contexte actuel tous les **\<Customer>** enfants :  
  
    ```  
    child::Customer  
    ```  
  
     Dans la requête XPath suivante, `child` est l'axe. `Customer` est le test de nœud.  
  
-   `parent`  
  
     Contient le parent du nœud du contexte.  
  
     L’expression XPath suivante sélectionne tous les **\<Customer>** parents des **\<Order>** enfants :  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Cette option est équivalente à la spécification de `child::Customer`. Dans cette requête XPath, `child` et `parent` sont les axes. `Customer` et `Order` sont les tests de nœud.  
  
-   `attribute`  
  
     Contient l'attribut du nœud du contexte.  
  
     L’expression XPath suivante sélectionne l’attribut **CustomerID** du nœud de contexte :  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   `self`  
  
     Contient le nœud du contexte lui-même.  
  
     L’expression XPath suivante sélectionne le nœud actuel s’il s’agit du **\<Order>** nœud :  
  
    ```  
    self::Order  
    ```  
  
     Dans cette requête XPath, `self` est l'axe et `Order` le test de nœud.  
  
  
