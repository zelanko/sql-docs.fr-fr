---
title: Langage SQL (SQL) | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019031"
---
# <a name="structured-query-language-sql"></a>SQL (Structured Query Language)
Un SGBD classique permet aux utilisateurs de stocker, d’accéder et de modifier les données d’une manière organisée et efficace. À l’origine, les utilisateurs de SGBD étaient des programmeurs. Accès aux données stockées nécessaires à l’écriture d’un programme dans un langage de programmation tel que COBOL. Bien que ces programmes soient souvent écrits pour présenter une interface conviviale à un utilisateur non technique, l’accès aux données lui-même nécessitait les services d’un programmeur compétent. L’accès occasionnel aux données n’était pas pratique.  
  
 Les utilisateurs n’étaient pas entièrement satisfaits de cette situation. Bien qu’ils puissent accéder aux données, il est souvent nécessaire de convaincre un programmeur SGBD d’écrire des Logiciels spéciaux. Par exemple, si un service commercial souhaite voir les ventes totales du mois précédent par chacun de ses représentants et souhaite que ces informations soient classées dans l’ordre de la durée de service de chaque commercial dans l’entreprise, il avait deux possibilités : soit un programme déjà présent a autorisé l’accès aux informations de cette manière exactement, ou le service devait demander à un programmeur d’écrire un tel programme. Dans de nombreux cas, il s’agissait d’une plus grande quantité de travail, et c’était toujours une solution coûteuse pour les recherches ponctuelles ou ad hoc. À mesure que de plus en plus d’utilisateurs voulaient un accès facile, ce problème a augmenté et est plus important.  
  
 Le fait de permettre aux utilisateurs d’accéder aux données sur une base ad hoc exigeait de leur donner une langue dans laquelle exprimer leurs demandes. Une requête unique à une base de données est définie en tant que requête. ce langage est appelé langage de requête. De nombreux langages de requête ont été développés à cet effet, mais l’un d’eux est devenu le plus populaire : langage SQL, inventé chez IBM au cours des années 1970. Il est plus communément appelé par son acronyme, SQL et est prononcé comme « ESS-CUE-Ell » et en tant que « faites ». SQL est devenu une norme ANSI dans 1986 et une norme ISO dans 1987. Il est utilisé aujourd’hui dans un grand nombre de systèmes de gestion de base de données.  
  
 Bien que SQL résolve les besoins des utilisateurs ad hoc, le besoin d’accès aux données par les programmes informatiques n’a pas disparu. En fait, la plupart des accès à la base de données étaient (et sont) par programmation, sous la forme de rapports régulièrement planifiés et d’analyses statistiques, de programmes de saisie de données tels que ceux utilisés pour la saisie de commandes et les programmes de manipulation de données, tels que ceux utilisés pour rapprocher les comptes et générer des ordres de travail.  
  
 Ces programmes utilisent également SQL, à l’aide de l’une des trois techniques suivantes :  
  
-   **Embedded SQL**, dans lequel les instructions SQL sont incorporées dans un langage hôte tel que C ou COBOL.  
  
-   **Modules SQL**, dans lesquels les instructions SQL sont compilées sur le SGBD et appelées à partir d’un langage hôte.  
  
-   **Interface de niveau d’appel**, ou CLI, qui se compose de fonctions appelées pour passer des instructions SQL au SGBD et récupérer les résultats du SGBD.  
  
> [!NOTE]  
>  Il s’agit d’un accident historique indiquant que le terme interface au niveau de l’appel est utilisé à la place de l’interface de programmation d’applications (API), un autre terme pour la même chose. Dans le monde de la base de données, l’API est utilisée pour décrire le SQL lui-même : SQL est l’API d’un SGBD.  
  
 Parmi ces choix, EmbeddedSQL est le plus couramment utilisé, bien que la plupart des SGBD principaux prennent en charge les CLI propriétaires.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Traitement d’une instruction SQL](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [Modules SQL](../../odbc/reference/sql-modules.md)  
  
-   [Interfaces de niveau d’appel](../../odbc/reference/call-level-interfaces.md)
