---
title: Quand utiliser des procédures | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], procedures
- procedures [ODBC], about procedures
ms.assetid: 7dc9e327-dd54-4b10-9f66-9ef5c074f122
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31aeea226bc8c8aa41f748d1d9a97d55147c4d67
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81289096"
---
# <a name="when-to-use-procedures"></a>Quand utiliser des procédures
L’utilisation de procédures présente un certain nombre d’avantages, tous basés sur le fait que l’utilisation de procédures déplace les instructions SQL de l’application vers la source de données. Ce qui reste dans l’application est un appel de procédure interopérable. Ces avantages sont les suivants :  
  
-   **Performances** Les procédures sont généralement le moyen le plus rapide d’exécuter des instructions SQL. Comme pour l’exécution préparée, l’instruction est compilée et exécutée en deux étapes distinctes. Contrairement à l’exécution préparée, les procédures sont exécutées uniquement au moment de l’exécution. Ils sont compilés à un autre moment.  
  
-   **Règles d’entreprise** Une *règle d’entreprise* est une règle relative à la façon dont une entreprise fait l’affaires. Par exemple, seule une personne ayant le titre de vendeur peut être autorisée à ajouter de nouvelles commandes. Le fait de placer ces règles dans des procédures permet aux sociétés individuelles de personnaliser les applications verticales en réécrivant les procédures appelées par l’application sans avoir à modifier le code de l’application. Par exemple, une application d’entrée de commande peut appeler la procédure **InsertOrder** avec un nombre fixe de paramètres. la façon dont **InsertOrder** est implémenté peut varier selon la société.  
  
-   **Remplacement** Les procédures peuvent être remplacées sans recompiler l’application, étroitement liées à la mise en place des règles d’entreprise dans les procédures. Si une règle d’entreprise change après qu’une société a acheté et installé une application, l’entreprise peut modifier la procédure contenant cette règle. Du point de vue de l’application, rien n’a changé. Il appelle toujours une procédure particulière pour accomplir une tâche particulière.  
  
-   **SQL spécifique au SGBD** Les procédures offrent aux applications un moyen d’exploiter le code SQL spécifique au SGBD tout en restant interopérables. Par exemple, une procédure sur un SGBD qui prend en charge les instructions de contrôle de passage dans SQL peut intercepter et récupérer des erreurs, tandis qu’une procédure sur un SGBD qui ne prend pas en charge les instructions de contrôle de Flow peut simplement retourner une erreur.  
  
-   Les **procédures survivent aux transactions** Sur certaines sources de données, les plans d’accès pour toutes les instructions préparées sur une connexion sont supprimés lorsqu’une transaction est validée ou annulée. En plaçant des instructions SQL dans des procédures, qui sont stockées de manière permanente dans la source de données, les instructions survivent à la transaction. La survie des procédures dans un état préparé, partiellement préparé ou non préparé est spécifique au SGBD.  
  
-   **Développement séparé** Les procédures peuvent être développées séparément du reste de l’application. Dans les grandes entreprises, cela peut permettre d’exploiter davantage les compétences des programmeurs hautement spécialisés. En d’autres termes, les programmeurs d’applications peuvent écrire du code d’interface utilisateur et des programmeurs de base de données peuvent écrire des procédures.  
  
 Les procédures sont généralement utilisées par les applications verticales et personnalisées. Ces applications ont tendance à effectuer des tâches fixes et il est possible de coder en dur les appels de procédure qu’elles contiennent. Par exemple, une application d’entrée de commande peut appeler les procédures **InsertOrder**, **DeleteOrder**, **UpdateOrder**et **GetOrders**.  
  
 Il y a peu de raisons d’appeler des procédures à partir d’applications génériques. Les procédures sont généralement écrites pour effectuer une tâche dans le contexte d’une application particulière et n’ont donc pas d’utilisation pour les applications génériques. Par exemple, une feuille de calcul n’a aucune raison d’appeler la procédure **InsertOrder** indiquée précédemment. En outre, les applications génériques ne doivent pas construire de procédures au moment de l’exécution dans l’espoir de fournir une exécution d’instruction plus rapide ; non seulement cela risque d’être plus lent que la préparation ou l’exécution directe, mais elle nécessite également des instructions SQL propres au SGBD.  
  
 Les environnements de développement d’applications constituent une exception, ce qui permet aux programmeurs de créer des instructions SQL qui exécutent des procédures et peuvent fournir aux programmeurs un moyen de tester les procédures. De tels environnements appellent **SQLProcedures** pour répertorier les procédures et les **SQLProcedureColumns** disponibles afin de répertorier les paramètres d’entrée, d’entrée/sortie et de sortie, la valeur de retour de la procédure et les colonnes de tous les jeux de résultats créés par une procédure. Toutefois, ces procédures doivent être développées au préalable sur chaque source de données ; Cela nécessite des instructions SQL propres au SGBD.  
  
 L’utilisation de procédures présente trois inconvénients majeurs. La première est que les procédures doivent être écrites et compilées pour chaque SGBD avec lequel l’application doit s’exécuter. Bien qu’il ne s’agit pas d’un problème pour les applications personnalisées, cela peut augmenter considérablement le temps de développement et de maintenance pour les applications verticales conçues pour s’exécuter avec un certain nombre de SGBD.  
  
 Le deuxième inconvénient est que de nombreux SGBD ne prennent pas en charge les procédures. Là encore, il s’agit probablement d’un problème pour les applications verticales conçues pour s’exécuter avec un certain nombre de SGBD. Pour déterminer si les procédures sont prises en charge, une application appelle **SQLGetInfo** avec l’option SQL_PROCEDURES.  
  
 Le troisième inconvénient, qui est particulièrement applicable aux environnements de développement d’applications, est qu’ODBC ne définit pas de grammaire standard pour la création de procédures. Autrement dit, bien que les applications puissent appeler des procédures de manière interactive, elles ne peuvent pas les créer interactives.
