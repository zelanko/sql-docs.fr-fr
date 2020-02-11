---
title: Prise en compte des fonctionnalités de base de données à utiliser | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67951878"
---
# <a name="considering-database-features-to-use"></a>Considérations sur les fonctionnalités de base de données à utiliser
Une fois le niveau d’interopérabilité de base connu, les fonctionnalités de base de données utilisées par l’application doivent être prises en compte. Par exemple, quelles sont les instructions SQL exécutées par l’application ? L’application utilisera-t-elle des curseurs à défilement ? Mouvements? Opératoire? Données de type long ? Pour obtenir des idées sur les fonctionnalités qui peuvent ne pas être prises en charge par tous les SGBD, consultez les descriptions des fonctions [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)et [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) , ainsi que l' [annexe C : syntaxe SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md). Les fonctionnalités requises par une application peuvent éliminer certains SGBD de la liste des SGBD cibles. Ils peuvent également indiquer que l’application peut facilement cibler de nombreux SGBD.  
  
 Par exemple, si les fonctionnalités requises sont simples, elles peuvent généralement être implémentées avec un degré élevé d’interopérabilité. Une application qui exécute une instruction **Select** simple et récupère les résultats avec un curseur avant uniquement est susceptible d’être très interopérable en raison de sa simplicité : presque tous les pilotes et SGBD prennent en charge les fonctionnalités dont ils ont besoin.  
  
 Toutefois, si les fonctionnalités requises sont plus complexes, telles que les curseurs de défilement, les instructions Update et DELETE positionnées et les procédures, il faut souvent faire des compromis. Il existe plusieurs possibilités :  
  
-   **Interopérabilité inférieure, plus de fonctionnalités.** L’application comprend les fonctionnalités, mais fonctionne uniquement avec les SGBD qui les prennent en charge.  
  
-   **Interopérabilité plus élevée, moins de fonctionnalités.** L’application dépose les fonctionnalités mais fonctionne avec davantage de SGBD.  
  
-   **Interopérabilité supérieure, fonctionnalités facultatives.** L’application comprend les fonctionnalités, mais les met à disposition uniquement avec les SGBD qui les prennent en charge.  
  
-   **Interopérabilité supérieure, plus de fonctionnalités.** L’application utilise les fonctionnalités avec des SGBD qui les prennent en charge et les émule pour les SGBD qui ne le sont pas.  
  
 Les deux premiers cas sont relativement simples à implémenter, car les fonctionnalités sont utilisées avec tous les SGBD pris en charge ou avec aucun. Les deux derniers cas, en revanche, sont plus complexes. Dans les deux cas, il est nécessaire de vérifier si le SGBD prend en charge les fonctionnalités et, dans le dernier cas, d’écrire un nombre potentiellement important de code pour émuler ces fonctionnalités. Par conséquent, ces schémas sont susceptibles de nécessiter plus de temps de développement et peuvent être plus lents au moment de l’exécution.  
  
 Prenons l’exemple d’une application de requête générique qui peut se connecter à une source de données unique. L’application accepte une requête de l’utilisateur et affiche les résultats dans une fenêtre. Supposons maintenant que cette application dispose d’une fonctionnalité qui permet aux utilisateurs d’afficher simultanément les résultats de plusieurs requêtes. Autrement dit, ils peuvent exécuter une requête et examiner certains résultats, exécuter une requête différente et examiner certains de ses résultats, puis revenir à la première requête. Cela présente un problème d’interopérabilité, car certains pilotes ne prennent en charge qu’une seule instruction active.  
  
 L’application a un certain nombre de choix, en fonction de ce que le pilote retourne pour l’option SQL_MAX_CONCURRENT_ACTIVITIES dans **SQLGetInfo**:  
  
-   **Prend toujours en charge plusieurs requêtes.** Une fois connecté à un pilote, l’application vérifie le nombre d’instructions actives. Si le pilote ne prend en charge qu’une seule instruction active, l’application ferme la connexion et informe l’utilisateur que le pilote ne prend pas en charge les fonctionnalités requises. L’application est facile à implémenter et dispose d’une fonctionnalité complète, mais elle a une interopérabilité plus faible.  
  
-   **Ne jamais prendre en charge plusieurs requêtes.** L’application dépose la fonctionnalité entièrement. Il est facile à implémenter et a une interopérabilité élevée, mais il a moins de fonctionnalités.  
  
-   **Prend en charge plusieurs requêtes uniquement si le pilote le fait.** Une fois connecté à un pilote, l’application vérifie le nombre d’instructions actives. L’application permet à l’utilisateur de démarrer une nouvelle instruction lorsque celle-ci est déjà active uniquement si le pilote prend en charge plusieurs instructions actives. L’application dispose d’une plus grande fonctionnalité et d’une meilleure interopérabilité, mais elle est plus difficile à implémenter.  
  
-   **Prenez toujours en charge plusieurs requêtes et émulez-les si nécessaire.** Une fois connecté à un pilote, l’application vérifie le nombre d’instructions actives. L’application permet toujours à l’utilisateur de démarrer une nouvelle instruction lorsque celle-ci est déjà active. Si le pilote ne prend en charge qu’une seule instruction active, l’application ouvre une connexion supplémentaire à ce pilote et exécute la nouvelle instruction sur cette connexion. L’application dispose de toutes les fonctionnalités et d’une grande interopérabilité, mais elle est plus difficile à implémenter.
