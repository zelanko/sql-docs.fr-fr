---
title: Langage de requête structurée (SQL) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC]
- SQL [ODBC], about SQL
- ODBC [ODBC], SQL
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c669b4424271fc1a3c91dea37159474fb52b97cd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293389"
---
# <a name="structured-query-language-sql"></a>SQL (Structured Query Language)
Un DBMS typique permet aux utilisateurs de stocker, d’accéder et de modifier les données d’une manière organisée et efficace. À l’origine, les utilisateurs de DBMS étaient des programmeurs. L’accès aux données stockées exigeait la rédaction d’un programme dans un langage de programmation tel que COBOL. Bien que ces programmes aient souvent été écrits pour présenter une interface amicale à un utilisateur non technique, l’accès aux données elle-même nécessitait les services d’un programmeur bien informé. L’accès occasionnel aux données n’était pas pratique.  
  
 Les utilisateurs n’étaient pas entièrement satisfaits de cette situation. Bien qu’ils puissent accéder aux données, il fallait souvent convaincre un programmeur DBMS d’écrire un logiciel spécial. Par exemple, si un service de vente voulait voir les ventes totales le mois précédent par chacun de ses vendeurs et voulait que cette information soit classée en ordre par la durée de service de chaque vendeur dans l’entreprise, elle avait deux choix : soit un programme existait déjà qui permettait d’accéder à l’information exactement de cette façon, soit le ministère devait demander à un programmeur d’écrire un tel programme. Dans de nombreux cas, il s’agissait de plus de travail qu’il n’en valait la peine, et c’était toujours une solution coûteuse pour les demandes ponctuelles ou ponctuelles. Comme de plus en plus d’utilisateurs voulaient un accès facile, ce problème est devenu de plus en plus grand.  
  
 Permettre aux utilisateurs d’accéder aux données sur une base ad hoc exigeait de leur donner un langage permettant d’exprimer leurs demandes. Une seule demande à une base de données est définie comme une requête; une telle langue est appelée une langue de requête. De nombreuses langues de requête ont été développées à cette fin, mais l’une d’entre elles est devenue la plus populaire : le langage de requête structurée, inventé chez IBM dans les années 1970. Il est plus communément connu sous son acronyme, SQL, et est prononcé à la fois comme "ess-cue-ell" et comme "suite". SQL est devenu une norme ANSI en 1986 et une norme ISO en 1987; il est utilisé aujourd’hui dans un grand nombre de systèmes de gestion de base de données.  
  
 Bien que SQL ait résolu les besoins ad hoc des utilisateurs, le besoin d’accès aux données par les programmes informatiques n’a pas disparu. En fait, la plupart des accès à la base de données étaient encore (et sont) programmatiques, sous forme de rapports et d’analyses statistiques réguliers, de programmes de saisie de données tels que ceux utilisés pour la saisie des commandes et de programmes de manipulation de données, comme ceux utilisés pour concilier les comptes et générer des ordres de travail.  
  
 Ces programmes utilisent également SQL, en utilisant l’une des trois techniques suivantes :  
  
-   **SqL intégré**, dans lequel les déclarations SQL sont intégrées dans une langue d’hôte comme C ou COBOL.  
  
-   **Modules SQL**, dans lesquels les déclarations SQL sont compilées sur le DBMS et appelées à partir d’une langue d’accueil.  
  
-   **Interface de niveau d’appel**, ou CLI, qui se compose de fonctions appelées à transmettre les relevés SQL à la DBMS et à récupérer les résultats de la DBMS.  
  
> [!NOTE]  
>  Il s’agit d’un accident historique que le terme interface de niveau d’appel est utilisé au lieu de l’interface de programmation d’application (API), un autre terme pour la même chose. Dans le monde de la base de données, l’API est utilisée pour décrire SQL elle-même : SQL est l’API d’un DBMS.  
  
 Parmi ces choix, le SQL intégré est le plus couramment utilisé, bien que la plupart des grands DBMS prennent en charge les IGC propriétaires.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Traitement d’une déclaration SQL](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [Modules SQL](../../odbc/reference/sql-modules.md)  
  
-   [Interfaces de niveau d’appel](../../odbc/reference/call-level-interfaces.md)
