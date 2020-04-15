---
title: Quand utiliser les procédures Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289096"
---
# <a name="when-to-use-procedures"></a>Quand utiliser des procédures
Il y a un certain nombre d’avantages à utiliser des procédures, tous basés sur le fait que l’utilisation des procédures déplace les déclarations SQL de l’application à la source de données. Ce qui reste dans l’application est un appel de procédure interopérable. Ces avantages comprennent :  
  
-   **Performance** Les procédures sont généralement le moyen le plus rapide d’exécuter les déclarations SQL. Comme l’exécution préparée, la déclaration est compilée et exécutée en deux étapes distinctes. Contrairement à l’exécution préparée, les procédures ne sont exécutées qu’au moment de l’exécution. Ils sont compilés à un moment différent.  
  
-   **Règles d’affaires** Une *règle d’affaires* est une règle sur la façon dont une entreprise fait des affaires. Par exemple, seule une personne ayant le titre Sales Person peut être autorisée à ajouter de nouvelles commandes de vente. L’imposition de ces règles dans les procédures permet aux entreprises individuelles de personnaliser les applications verticales en réécrivant les procédures appelées par l’application sans avoir à modifier le code d’application. Par exemple, une demande d’entrée de commande peut appeler la procédure **InsertOrder** avec un nombre fixe de paramètres; exactement comment **InsertOrder** est implémenté peut varier d’une entreprise à l’autre.  
  
-   **Remplacer** Le fait que les procédures peuvent être remplacées sans recompiler la demande est étroitement liée à l’établissement de règles commerciales dans les procédures. Si une règle d’entreprise change après qu’une entreprise a acheté et installé une application, l’entreprise peut modifier la procédure contenant cette règle. Du point de vue de l’application, rien n’a changé; il appelle toujours une procédure particulière pour accomplir une tâche particulière.  
  
-   **SQL spécifique à DBMS** Les procédures permettent aux applications d’exploiter la SQL spécifique à DBMS tout en demeurant interopérables. Par exemple, une procédure sur un DBMS qui prend en charge les déclarations de contrôle de débit dans SQL pourrait piéger et se remettre d’erreurs, tandis qu’une procédure sur un DBMS qui ne prend pas en charge les déclarations de contrôle du flux peut simplement retourner une erreur.  
  
-   **Les procédures survivent aux transactions** Sur certaines sources de données, les plans d’accès pour toutes les déclarations préparées sur une connexion sont supprimés lorsqu’une transaction est validée ou annulée. En plaçant des relevés SQL dans les procédures, qui sont stockées en permanence dans la source de données, les déclarations survivent à la transaction. La question de savoir si les procédures survivent dans un état préparé, partiellement préparé ou non préparé est spécifique à DBMS.  
  
-   **Développement séparé** Les procédures peuvent être développées séparément du reste de l’application. Dans les grandes entreprises, cela pourrait fournir un moyen d’exploiter davantage les compétences des programmeurs hautement spécialisés. En d’autres termes, les programmeurs d’applications peuvent écrire du code d’interface utilisateur et les programmeurs de bases de données peuvent écrire des procédures.  
  
 Les procédures sont généralement utilisées par des applications verticales et personnalisées. Ces applications ont tendance à effectuer des tâches fixes, et il est possible d’appeler la procédure de code dur en eux. Par exemple, une application d’entrée de commande peut appeler les procédures **InsertOrder**, **DeleteOrder**, **UpdateOrder**, et **GetOrders**.  
  
 Il y a peu de raisons d’appeler les procédures des applications génériques. Les procédures sont généralement écrites pour effectuer une tâche dans le cadre d’une application particulière et n’ont donc aucune utilité pour les applications génériques. Par exemple, une feuille de calcul n’a aucune raison d’appeler la procédure InsertOrder qui vient **d’être** mentionnée. En outre, les applications génériques ne devraient pas construire de procédures à l’heure d’exécution dans l’espoir de fournir une exécution plus rapide des relevés; non seulement cela est susceptible d’être plus lent que l’exécution préparée ou directe, mais il nécessite également des déclarations SQL propres à DBMS.  
  
 Une exception à cette règle est les environnements de développement d’applications, qui fournissent souvent un moyen pour les programmeurs de construire des déclarations SQL qui exécutent des procédures et peuvent fournir un moyen pour les programmeurs de tester les procédures. Ces environnements appellent **SQLProcedures** pour énumérer les procédures disponibles et **SQLProcedureColumns** pour énumérer les paramètres d’entrée, d’entrée/sortie et de sortie, la valeur de retour de procédure et les colonnes de tous les ensembles de résultats créés par une procédure. Toutefois, de telles procédures doivent être élaborées à l’avance sur chaque source de données; pour ce faire, il faut des déclarations SQL spécifiques à DBMS.  
  
 L’utilisation des procédures est de trois inconvénients majeurs. La première est que les procédures doivent être écrites et compilées pour chaque DBMS avec lequel l’application doit s’exécuter. Bien que ce n’est pas un problème pour les applications personnalisées, il peut augmenter considérablement le temps de développement et de maintenance pour les applications verticales conçues pour fonctionner avec un certain nombre de DBMS.  
  
 Le deuxième inconvénient est que de nombreux DBMS ne prennent pas en charge les procédures. Encore une fois, il est plus probable que ce soit un problème pour les applications verticales conçues pour fonctionner avec un certain nombre de DBMS. Pour déterminer si les procédures sont prises en charge, une demande appelle **SQLGetInfo** avec l’option SQL_PROCEDURES.  
  
 Le troisième inconvénient, qui s’applique particulièrement aux environnements de développement d’applications, est que l’ODBC ne définit pas une grammaire standard pour la création de procédures. Autrement dit, bien que les applications puissent appeler des procédures interopératoirement, elles ne peuvent pas les créer interopérablement.
