---
title: À l’aide de la syntaxe dans une Expression de chemin d’accès abrégée | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- abbreviated syntax [XQuery]
ms.assetid: f83c2e41-5722-47c3-b5b8-bf0f8cbe05d3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ee9a48b4bec625e4d64caf20aa1b5c8eaefe34f3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660398"
---
# <a name="path-expressions---using-abbreviated-syntax"></a>Expressions de chemin : utilisation de la syntaxe abrégée
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Tous les exemples de [présentation des Expressions de chemin d’accès dans XQuery](../xquery/path-expressions-xquery.md) utiliser la syntaxe non abrégée pour les expressions de chemin d’accès. La syntaxe non abrégée pour une étape d'axe dans une expression de chemin d'accès inclut le nom de l'axe et le test du nœud, séparés par un double signe deux-points et suivis le cas échéant par des qualificatifs d'étape.  
  
 Exemple :  
  
```  
child::ProductDescription[attribute::ProductModelID=19]  
```  
  
 XQuery prend en charge les abréviations suivantes lors de l'utilisation d'expressions de chemin d'accès :  
  
-   Le **enfant** axe est l’axe par défaut. Par conséquent, le **enfant ::** peut être omis à partir d’une étape dans une expression. Par exemple, `/child::ProductDescription/child::Summary` peut s'écrire sous la forme `/ProductDescription/Summary`.  
  
-   Un **attribut** axe peut être abrégé par @. Par exemple, `/child::ProductDescription[attribute::ProductModelID=10]` peut s'écrire sous la forme `/ProudctDescription[@ProductModelID=10]`.  
  
-   Un **/descendant-or-self::node()/** peut être abrégé par / /. Par exemple, `/descendant-or-self::node()/child::act:telephoneNumber` peut s'écrire sous la forme `//act:telephoneNumber`.  
  
     La requête précédente récupère tous les numéros de téléphone stockés dans la colonne AdditionalContactInfo de la table Contact. Le schéma pour AdditionalContactInfo est défini d’une manière qui un \<telephoneNumber > élément peut apparaître n’importe où dans le document. Ainsi, pour retrouver tous les numéros de téléphone, vous devez rechercher tous les nœuds du document. Cette recherche part de la racine du document et se poursuit à travers tous les nœuds descendants.  
  
     La requête suivante permet de récupérer tous les numéros de téléphone pour un client donné d'après ses informations de contact :  
  
    ```  
    SELECT AdditionalContactInfo.query('             
                declare namespace act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";             
                declare namespace crm="https://schemas.adventure-works.com/Contact/Record";             
                declare namespace ci="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";             
                /descendant-or-self::node()/child::act:telephoneNumber             
                ') as result             
    FROM Person.Contact             
    WHERE ContactID=1             
    ```  
  
     Si vous remplacez l'expression de chemin d'accès par sa syntaxe abrégée `//act:telephoneNumber`, vous obtenez les mêmes résultats.  
  
-   Le **self ::node()** dans une étape peut être abrégé en un seul point (.). Toutefois, le point n’est ni équivalent ni interchangeable avec le **self ::node()**.  
  
     Par exemple, utiliser un point dans la requête suivante revient à représenter une valeur et non un nœud :  
  
    ```  
    ("abc", "cde")[. > "b"]  
    ```  
  
-   Le **parent ::node()** dans une étape peut être abrégé par deux points (.).  
  
  
