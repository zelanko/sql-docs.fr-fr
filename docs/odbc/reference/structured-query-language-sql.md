---
title: Structured Query Language (SQL) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6cae344e97bf6e5dc8affbf164f80eb8935846e1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68019031"
---
# <a name="structured-query-language-sql"></a>SQL (Structured Query Language)
Un SGBD classique permet aux utilisateurs de stocker, accéder et modifier des données d’une façon organisée et efficace. À l’origine, les utilisateurs de SGBD ont été les programmeurs. L’accès aux données stockées exigeaient l’écriture d’un programme dans un langage de programmation tels que COBOL. Bien que ces programmes ont été écrits souvent à présenter une interface conviviale à un utilisateur non technique, l’accès aux données elles-mêmes requis les services d’un programmeur expérimenté. Accès aisé aux données n’était pas pratique.  
  
 Les utilisateurs n’étaient pas entièrement satisfaits de cette situation. Pendant qu’ils pourraient accéder aux données, il est souvent nécessaire de convaincre un programmeur de SGBD pour écrire un logiciel spécial. Par exemple, si un service des ventes pour voir le total des ventes du mois précédent par chacun de ses commerciaux et vouliez ces informations classées dans l’ordre selon la longueur de chaque représentant du service de l’entreprise, il avait deux possibilités : Un programme existait déjà autorisés les informations accessibles exactement de cette manière, ou le service ne se pose un programmeur pour écrire un programme de ce type. Dans de nombreux cas, il s’agissait de plus de travail qu’il valait la peine, et il a toujours été une solution coûteuse pour des requêtes à usage unique ou ad hoc. Comme le plus grand d’utilisateurs souhaitait accéder facilement, ce problème a augmenté de plus en plus grandes.  
  
 Permettre aux utilisateurs d’accéder aux données sur une base ad hoc requis en leur donnant une langue dans laquelle exprimer leurs demandes. Une demande unique à une base de données est définie en tant que requête ; ces langages sont appelé un langage de requête. Nombreux langages de requête ont été développés à cet effet, mais un d’eux est devenu le plus courant : Structured Query Language, inventé IBM dans les années 1970. Il est plus communément appelée par son acronyme, SQL et est prononcé à la fois en tant que « ess-cue-ell » et « suite ». SQL est devenu un ANSI standard en 1986 et un fichier ISO standard en 1987 ; Il est utilisé aujourd'hui dans des nombreux systèmes de gestion de base de données.  
  
 Bien que SQL résolu des besoins des utilisateurs ad hoc, la nécessité d’accès aux données par les applications ne pas disparu. En fait, la plupart des accès de base de données toujours était (et est) par programmation, sous la forme des rapports régulièrement planifiées et des analyses statistiques, entrée de données des programmes tels que ceux utilisés pour la saisie de commandes et les données des programmes de manipulation, telles que celles utilisées pour harmoniser les comptes et générer les ordres de travail.  
  
 Ces programmes utilisent également SQL, à l’aide d’une des trois techniques suivantes :  
  
-   **Embedded SQL**, dans lequel SQL instructions sont incorporées dans un langage hôte tels que C ou COBOL.  
  
-   **Modules SQL**, dans les instructions SQL sont compilées dans le SGBD et appelées à partir d’un langage hôte.  
  
-   **Interface de niveau d’appel**, ou l’interface CLI, qui se compose des fonctions appelées pour passer des instructions SQL au SGBD et pour récupérer les résultats de SGBD.  
  
> [!NOTE]  
>  Il s’agit d’un incident historique qui créent une interface le terme interface au niveau de l’appel est utilisée au lieu de la programmation d’applications (API), un autre terme pour la même chose. Dans le monde de la base de données, l’API est utilisée pour décrire SQL lui-même : SQL est l’API à un SGBD.  
  
 De ces choix, embedded SQL est le plus couramment utilisé, bien que la plupart des SGBD majeure prennent en charge les interfaces CLI propriétaires.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Traitement d’une instruction SQL](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [Modules SQL](../../odbc/reference/sql-modules.md)  
  
-   [Interfaces de niveau d’appel](../../odbc/reference/call-level-interfaces.md)
