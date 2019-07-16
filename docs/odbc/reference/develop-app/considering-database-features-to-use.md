---
title: Prise en compte les fonctionnalités de base de données à utiliser | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], database features
ms.assetid: 59760114-508e-46c5-81d2-8f2498c0d778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3a945eef43a1fc12689853c3fa209f6126df4f0d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951878"
---
# <a name="considering-database-features-to-use"></a>Considérations sur les fonctionnalités de base de données à utiliser
Une fois le niveau de base d’interopérabilité est connu, les fonctionnalités de base de données utilisées par l’application doivent être examinées. Par exemple, les instructions SQL que l’application exécutera ? L’application va utiliser des curseurs avec défilement ? Transactions ? Procédures ? Données de type long ? Pour obtenir des suggestions sur les fonctionnalités ne peuvent pas pris en charge par tous les SGBD, consultez le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), et [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) les descriptions de fonction et [ Annexe c : Grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Les fonctionnalités requises par une application peuvent éliminer certains SGBD à partir de la liste des cibles SGBD. Il peuvent également indiquer que l’application peut cibler facilement les nombreux SGBD.  
  
 Par exemple, si les fonctionnalités requises sont simples, elles peuvent être implémentées généralement avec un degré élevé d’interopérabilité. Une application qui exécute une simple **sélectionnez** instruction et récupère les résultats avec un curseur avant uniquement est susceptible d’être hautement interopérable en vertu de sa simplicité : Presque tous les pilotes et les SGBD prennent en charge les fonctionnalités dont il a besoin.  
  
 Toutefois, si les fonctionnalités requises sont plus complexes, telles que des procédures et instructions delete, curseurs avec défilement et mise à jour positionnée, compromis doivent souvent être établies. Il existe plusieurs possibilités :  
  
-   **Interopérabilité plus faible, plus de fonctionnalités.** L’application inclut les fonctionnalités, mais fonctionne uniquement avec les SGBD qui les prennent en charge.  
  
-   **Interopérabilité plus élevée, moins de fonctionnalités.** L’application supprime les fonctionnalités, mais fonctionne avec plus de SGBD.  
  
-   **Interopérabilité plus élevée, des fonctionnalités facultatives.** L’application inclut les fonctionnalités, mais les rend disponibles uniquement avec ces SGBD qui les prennent en charge.  
  
-   **Interopérabilité plus élevée, plus de fonctionnalités.** L’application utilise les fonctionnalités avec SGBD qui les prennent en charge et émule les pour SGBD qui ne le faites pas.  
  
 Les deux premiers cas sont relativement simples à implémenter, car les fonctionnalités sont utilisées avec tous les SGBD pris en charge ou none. Les deux derniers cas, quant à eux, sont plus complexes. Il est nécessaire dans les deux cas pour vérifier si le SGBD prend en charge les fonctionnalités et dans le dernier cas pour écrire une grande quantité potentielle de code pour émuler ces fonctionnalités. Par conséquent, ces schémas sont susceptibles de nécessiter plus de temps de développement et peuvent être plus lentes au moment de l’exécution.  
  
 Imaginez une application de requête générique pouvant se connecter à une source de données. L’application accepte une requête à partir de l’utilisateur et affiche les résultats dans une fenêtre. Maintenant Supposons que cette application possède une fonctionnalité qui permet aux utilisateurs d’afficher les résultats de plusieurs requêtes simultanément. Autrement dit, ils peuvent exécuter une requête Examinons quelques-unes des résultats, exécuter une requête différente et examinons quelques-unes de ses résultats et puis revenez à la première requête. Cela pose un problème d’interopérabilité, car certains pilotes prennent en charge une seule instruction active.  
  
 L’application a un certain nombre de choix, selon ce que le pilote retourne pour l’option SQL_MAX_CONCURRENT_ACTIVITIES dans **SQLGetInfo**:  
  
-   **Toujours prendre en charge plusieurs requêtes.** Après vous être connecté à un pilote, l’application vérifie le nombre d’instructions actives. Si le pilote prend en charge qu’une seule instruction active, l’application ferme la connexion et informe l’utilisateur que le pilote ne prend pas en charge les fonctionnalités requises. L’application est facile à implémenter et toutes les fonctionnalités, mais a l’interopérabilité inférieur.  
  
-   **Jamais prend en charge plusieurs requêtes.** L’application supprime complètement la fonctionnalité. Il est facile à implémenter et a une interopérabilité élevée mais moins de fonctionnalités.  
  
-   **Prend en charge plusieurs requêtes uniquement si le pilote effectue.** Après vous être connecté à un pilote, l’application vérifie le nombre d’instructions actives. L’application permet à l’utilisateur démarrer une nouvelle instruction lorsqu’une est déjà active uniquement si le pilote prend en charge plusieurs instructions actives. L’application a le plus élevé de fonctionnalité et d’interopérabilité, mais est plus difficile à implémenter.  
  
-   **Toujours prendre en charge plusieurs requêtes et émuler lorsque cela est nécessaire.** Après vous être connecté à un pilote, l’application vérifie le nombre d’instructions actives. L’application always permet à l’utilisateur démarrer une nouvelle instruction lorsqu’une est déjà active. Si le pilote prend en charge qu’une seule instruction active, l’application ouvre une connexion supplémentaire à ce pilote et exécute la nouvelle instruction sur cette connexion. L’application a toutes les fonctionnalités et interopérabilité élevée, mais est plus difficile à implémenter.
