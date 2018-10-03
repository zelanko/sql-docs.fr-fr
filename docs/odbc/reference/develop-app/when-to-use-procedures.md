---
title: Quand utiliser les procédures | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82e71e6849902eb2f02423560c534056112a139a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854517"
---
# <a name="when-to-use-procedures"></a>Quand utiliser des procédures
Il existe un certain nombre d’avantages à l’aide de procédures, tous fait que l’utilisation des procédures déplace les instructions SQL à partir de l’application à la source de données. Ce qui est conservé dans l’application est un appel de procédure interopérable. Ces avantages :  
  
-   **Performances** procédures sont généralement plus rapide d’exécuter des instructions SQL. Comme l’exécution de préparée, l’instruction est compilée et exécutée en deux étapes distinctes. Contrairement à l’exécution préparée, les procédures sont exécutées uniquement au moment de l’exécution. Elles sont compilées à un autre moment.  
  
-   **Les règles d’entreprise** A *règle d’entreprise* est une règle sur la façon dont exerçant dans lequel une entreprise. Par exemple, seules les personnes ayant le titre commercial peuvent être autorisé à ajouter des nouvelles commandes client. Placer ces règles dans les procédures permet de personnaliser des applications verticales en réécrivant les procédures appelées par l’application sans avoir à modifier le code d’application des entreprises. Par exemple, une application de saisie de commandes peut appeler la procédure **InsertOrder** avec un nombre fixe de paramètres ; exactement comment **InsertOrder** est implémentée peut varier d’une entreprise à l’autre.  
  
-   **Replaceability** étroitement liées au placement des règles d’entreprise dans les procédures est le fait que les procédures peuvent être remplacées sans recompiler l’application. Si une règle d’entreprise change après qu’une entreprise a acheté et installé une application, la société peut modifier la procédure qui la contient. Du point de vue de l’application, rien n’a changé ; Il appelle toujours une procédure particulière pour accomplir une tâche particulière.  
  
-   **Propres au SGBD SQL** procédures fournissent un moyen aux applications d’exploiter SGBD spécifiques SQL et se trouvent toujours interopérable. Par exemple, une procédure sur un SGBD qui prend en charge les instructions de contrôle de flux dans SQL peut intercepter et récupérer les erreurs, tandis qu’une procédure sur un SGBD qui ne prend pas en charge les instructions de contrôle de flux simplement renvoyer une erreur.  
  
-   **Procédures survivent aux transactions** après certaines sources de données, les plans d’accès pour les instructions préparées tout sur une connexion sont supprimés lorsqu’une transaction est validée ou restaurée. En plaçant des instructions SQL dans les procédures, qui sont stockés définitivement dans la source de données, les instructions survivre à la transaction. Si les procédures survivent dans préparée, partiellement préparé, ou état non préparé est spécifique au SGBD.  
  
-   **Séparer développement** procédures peuvent être développés séparément du reste de l’application. Dans les grandes entreprises, cela peut constituer un moyen pour exploiter davantage les compétences des programmeurs hautement spécialisées. En d’autres termes, les programmeurs d’applications peuvent écrire du code de l’interface utilisateur et les programmeurs de base de données peuvent écrire des procédures.  
  
 Les procédures sont généralement utilisés par les applications verticales et personnalisées. Ces applications ont tendance à effectuer des tâches fixes, et il est possible d’appels de procédure de coder en dur dans les. Par exemple, une application de saisie de commandes peut appeler les procédures **InsertOrder**, **DeleteOrder**, **UpdateOrder**, et **GetOrders** .  
  
 Il y a peu de raisons pour appeler des procédures à partir d’applications génériques. Procédures sont généralement écrits pour effectuer une tâche dans le contexte d’une application particulière et donc d’aucune utilité pour les applications génériques. Par exemple, une feuille de calcul n’a aucune raison d’appeler le **InsertOrder** procédure précité. En outre, les applications génériques ne doivent pas construire de procédures en cours d’exécution dans l’exécution d’instruction plus rapide ; est non seulement ce susceptibles d’être plus lente que l’exécution préparée ou directe, elle nécessite également des instructions propres au SGBD SQL.  
  
 Une exception est les environnements de développement d’applications, qui offrent souvent une manière aux programmeurs de créer des instructions SQL qui exécutent des procédures et peuvent fournir un moyen pour les programmeurs tester les procédures. Appel de ces environnements **SQLProcedures** aux procédures disponibles de liste et **SQLProcedureColumns** pour répertorier les paramètres d’entrée, d’entrée/sortie et sortie, la procédure de valeur de retour et les colonnes de les jeux de résultats créés par une procédure. Toutefois, ces procédures doivent être développées au préalable sur chaque source de données ; Cette opération requiert des instructions propres au SGBD SQL.  
  
 Il existe trois inconvénients principaux à l’aide de procédures. La première est que les procédures doivent être écrits et compilés pour chaque SGBD avec lequel l’application consiste à exécuter. Bien que cela ne soit pas un problème pour les applications personnalisées, il peut augmenter considérablement développement et l’heure de maintenance pour les applications verticales conçu pour s’exécuter avec un nombre de SGBD.  
  
 Le deuxième inconvénient est que nombreux SGBD ne prennent pas en charge les procédures. Là encore, il s’agit probablement d’être un problème pour les applications verticales conçu pour s’exécuter avec un nombre de SGBD. Pour déterminer si les procédures sont prises en charge, une application appelle **SQLGetInfo** avec l’option SQL_PROCEDURES.  
  
 Le troisième, qui est particulièrement aux environnements de développement d’application, inconvénient que ODBC ne définit pas une syntaxe standard pour la création de procédures. Autrement dit, bien que les applications peuvent appeler des procédures plus, ils ne peuvent pas créer plus.
