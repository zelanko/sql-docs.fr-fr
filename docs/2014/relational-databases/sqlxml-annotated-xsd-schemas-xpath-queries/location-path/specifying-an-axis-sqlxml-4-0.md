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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8da239fd8a6bbf559f89ba5fd1b0fa0ab10ec190
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66012648"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Spécification d'un axe (SQLXML 4.0)
    
-   L'axe spécifie la relation d'arborescence entre les nœuds sélectionnés par l'étape d'emplacement et le nœud de contexte. Les axes suivants sont admis :`child`  
  
     Contient l'enfant du nœud du contexte.  
  
     L’expression XPath suivante (chemin d’accès d’emplacement) sélectionne à partir du nœud de contexte actuel tout le ** \<client>** enfants :  
  
    ```  
    child::Customer  
    ```  
  
     Dans la requête XPath suivante, `child` est l'axe. `Customer` est le test de nœud.  
  
-   `parent`  
  
     Contient le parent du nœud du contexte.  
  
     L’expression XPath suivante sélectionne tous les ** \<clients>** parents de l' ** \<ordre>** enfants :  
  
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
  
     L’expression XPath suivante sélectionne le nœud actuel s’il s’agit de l' ** \<ordre>** nœud :  
  
    ```  
    self::Order  
    ```  
  
     Dans cette requête XPath, `self` est l'axe et `Order` le test de nœud.  
  
  
