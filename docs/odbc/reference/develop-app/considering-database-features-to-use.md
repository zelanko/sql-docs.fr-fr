---
title: Considérant les fonctionnalités de base de données à utiliser Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9d966781def1c3eab6a9568eab07ab591326171
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299009"
---
# <a name="considering-database-features-to-use"></a>Considérations sur les fonctionnalités de base de données à utiliser
Une fois le niveau de base d’interopérabilité connu, les fonctionnalités de base utilisées par l’application doivent être prises en considération. Par exemple, quelles déclarations SQL l’application exécutera-t-elle? L’application utilisera-t-elle des curseurs défilementables ? Transactions? Procédures? De longues données ? Pour des idées sur les caractéristiques qui pourraient ne pas être pris en charge par tous les DBMS, voir le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), et [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) descriptions de la fonction, et [Annexe C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Les caractéristiques requises par une application pourraient éliminer certains DBMS de la liste des DBMS cibles. Ils peuvent également montrer que l’application peut facilement cibler de nombreux DBMS.  
  
 Par exemple, si les fonctionnalités requises sont simples, elles peuvent généralement être implémentées avec un degré élevé d’interopérabilité. Une application qui exécute une simple instruction **SELECT** et récupère les résultats avec un curseur avant-seulement est susceptible d’être hautement interopérable en raison de sa simplicité: Presque tous les pilotes et DBMS prennent en charge la fonctionnalité dont il a besoin.  
  
 Toutefois, si les fonctionnalités requises sont plus complexes, telles que les curseurs défilementables, les instructions de mise à jour et de suppression positionnées et les procédures, les compromis doivent souvent être effectués. Il existe plusieurs possibilités :  
  
-   **Moins d’interopérabilité, plus de fonctionnalités.** L’application comprend les fonctionnalités, mais ne fonctionne qu’avec DBMS qui les prennent en charge.  
  
-   **Une interopérabilité plus élevée, moins de fonctionnalités.** L’application laisse tomber les fonctionnalités, mais fonctionne avec plus de DBMS.  
  
-   **Une interopérabilité plus élevée, des caractéristiques facultatives.** L’application comprend les fonctionnalités, mais les rend disponibles uniquement avec les DBMS qui les prennent en charge.  
  
-   **Une interopérabilité plus élevée, plus de fonctionnalités.** L’application utilise les fonctionnalités avec DBMS qui les prennent en charge et les imite pour les DBMS qui ne le font pas.  
  
 Les deux premiers cas sont relativement simples à implémenter, car les fonctionnalités sont utilisées soit avec tous les DBMS pris en charge ou avec aucun. Les deux derniers cas, en revanche, sont plus complexes. Il est nécessaire dans les deux cas de vérifier si le DBMS prend en charge les fonctionnalités et dans le dernier cas d’écrire une quantité potentiellement importante de code pour émuler ces fonctionnalités. Par conséquent, ces régimes sont susceptibles de nécessiter plus de temps de développement et peuvent être plus lents au moment de l’exécution.  
  
 Considérez une application de requête générique qui peut se connecter à une seule source de données. L’application accepte une requête de l’utilisateur et affiche les résultats dans une fenêtre. Supposons maintenant que cette application dispose d’une fonctionnalité qui permet aux utilisateurs d’afficher simultanément les résultats de plusieurs requêtes. C’est-à-dire qu’ils peuvent exécuter une requête et regarder certains des résultats, exécuter une requête différente et regarder certains de ses résultats, puis revenir à la première requête. Cela présente un problème d’interopérabilité parce que certains conducteurs ne prennent en charge qu’une seule déclaration active.  
  
 L’application a un certain nombre de choix, en fonction de ce que le conducteur retourne pour l’option SQL_MAX_CONCURRENT_ACTIVITIES dans **SQLGetInfo**:  
  
-   **Soutenez toujours plusieurs requêtes.** Après s’être connecté à un conducteur, l’application vérifie le nombre d’instructions actives. Si le conducteur ne prend en charge qu’une seule déclaration active, l’application ferme la connexion et informe l’utilisateur que le pilote ne prend pas en charge les fonctionnalités requises. L’application est facile à implémenter et a une fonctionnalité complète, mais a une interopérabilité plus faible.  
  
-   **Ne jamais prendre en charge plusieurs requêtes.** L’application laisse tomber la fonctionnalité tout à fait. Il est facile à implémenter et a une interopérabilité élevée, mais a moins de fonctionnalités.  
  
-   **Prendre en charge plusieurs requêtes uniquement si le conducteur le fait.** Après s’être connecté à un conducteur, l’application vérifie le nombre d’instructions actives. L’application permet à l’utilisateur de démarrer une nouvelle déclaration lorsque celle-ci n’est déjà active que si le pilote prend en charge plusieurs instructions actives. L’application a une fonctionnalité et une interopérabilité plus élevées, mais est plus difficile à implémenter.  
  
-   **Soutenez toujours plusieurs requêtes et les émulez si nécessaire.** Après s’être connecté à un conducteur, l’application vérifie le nombre d’instructions actives. L’application permet toujours à l’utilisateur de démarrer une nouvelle déclaration lorsqu’elle est déjà active. Si le conducteur ne prend en charge qu’une seule déclaration active, l’application ouvre une connexion supplémentaire à ce pilote et exécute la nouvelle déclaration sur cette connexion. L’application a la pleine fonctionnalité et l’interopérabilité élevée, mais est plus difficile à implémenter.
