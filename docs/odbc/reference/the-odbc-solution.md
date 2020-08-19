---
description: La solution ODBC
title: La solution ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], using ODBC
ms.assetid: 34b80790-e010-4b90-8eaa-03189f5d8986
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f1a1c216dc67c33eadc9a058263087978f176297
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428861"
---
# <a name="the-odbc-solution"></a>La solution ODBC
La question, puis, est de la normalisation de l’accès aux bases de données par ODBC ? Il existe deux exigences architecturales :  
  
-   Les applications doivent être en mesure d’accéder à plusieurs SGBD à l’aide du même code source sans recompilation ni réédition de liens.  
  
-   Les applications doivent être en mesure d’accéder simultanément à plusieurs SGBD.  
  
 Et il existe une question supplémentaire, en raison de la réalité de la place de marché :  
  
-   Quelles sont les fonctionnalités SGBD qui doivent être exposées par ODBC ? Uniquement les fonctionnalités qui sont communes à tous les SGBD ou toutes les fonctionnalités disponibles dans n’importe quel SGBD ?  
  
 ODBC résout ces problèmes de la manière suivante :  
  
-   **ODBC est une interface au niveau de l’appel.** Pour résoudre le problème lié à la façon dont les applications accèdent à plusieurs SGBD à l’aide du même code source, ODBC définit une interface CLI standard. Elle contient toutes les fonctions des spécifications CLI de Open Group et ISO/IEC et fournit des fonctions supplémentaires généralement requises par les applications.  
  
     Une autre bibliothèque, ou pilote, est nécessaire pour chaque SGBD qui prend en charge ODBC. Le pilote implémente les fonctions dans l’API ODBC. Pour utiliser un autre pilote, il n’est pas nécessaire de recompiler ou de réassocier l’application. Au lieu de cela, l’application charge simplement le nouveau pilote et appelle les fonctions qu’elle contient. Pour accéder simultanément à plusieurs SGBD, l’application charge plusieurs pilotes. La prise en charge des pilotes est spécifique au système d’exploitation. Par exemple, sur le système d’exploitation Microsoft® Windows®, les pilotes sont des bibliothèques de liens dynamiques (dll).  
  
-   **ODBC définit une grammaire SQL standard.** En plus d’une interface standard au niveau de l’appel, ODBC définit une syntaxe SQL standard. Cette grammaire est basée sur la spécification Open Group d’IAO SQL. Les différences entre les deux grammaires sont mineures et principalement en raison des différences entre la grammaire SQL requise par Embedded SQL (Open Group) et une interface CLI (ODBC). Il existe également des extensions de la grammaire pour exposer les fonctionnalités de langage couramment disponibles qui ne sont pas couvertes par la grammaire de groupe ouverte.  
  
     Les applications peuvent envoyer des instructions à l’aide de la grammaire spécifique à ODBC ou au SGBD. Si une instruction utilise la grammaire ODBC qui est différente de la grammaire spécifique au SGBD, le pilote la convertit avant de l’envoyer à la source de données. Toutefois, ces conversions sont rares, car la plupart des SGBD utilisent déjà la grammaire SQL standard.  
  
-   **ODBC fournit un gestionnaire de pilotes pour gérer l’accès simultané à plusieurs SGBD.** Bien que l’utilisation de pilotes résout le problème lié à l’accès simultané à plusieurs SGBD, le code permettant de le faire peut être complexe. Les applications conçues pour fonctionner avec tous les pilotes ne peuvent pas être liées de manière statique à des pilotes. Au lieu de cela, ils doivent charger des pilotes au moment de l’exécution et appeler les fonctions qu’ils contiennent à l’aide d’une table de pointeurs de fonction. La situation devient plus complexe si l’application utilise plusieurs pilotes simultanément.  
  
     Plutôt que de forcer chaque application à le faire, ODBC fournit un gestionnaire de pilotes. Le gestionnaire de pilotes implémente toutes les fonctions ODBC, principalement comme des appels directs à des fonctions ODBC dans les pilotes, et est lié de manière statique à l’application ou chargé par l’application au moment de l’exécution. Ainsi, l’application appelle les fonctions ODBC par nom dans le gestionnaire de pilotes, plutôt qu’en fonction du pointeur de chaque pilote.  
  
     Lorsqu’une application a besoin d’un pilote particulier, elle demande tout d’abord un descripteur de connexion avec lequel identifier le pilote, puis demande que le gestionnaire de pilotes charge le pilote. Le gestionnaire de pilotes charge le pilote et stocke l’adresse de chaque fonction dans le pilote. Pour appeler une fonction ODBC dans le pilote, l’application appelle cette fonction dans le gestionnaire de pilotes et transmet le descripteur de connexion pour le pilote. Le gestionnaire de pilotes appelle ensuite la fonction à l’aide de l’adresse qu’il a stockée précédemment.  
  
-   **ODBC expose un nombre important de fonctionnalités de SGBD, mais ne requiert pas de pilotes pour les prendre en charge.** Si ODBC exposait uniquement des fonctionnalités communes à tous les SGBD, cela ne serait pas très utile. Après tout, la raison pour laquelle de nombreux SGBD existent aujourd’hui est qu’ils ont des fonctionnalités différentes. Si ODBC exposait chaque fonctionnalité disponible dans n’importe quel SGBD, il serait impossible que les pilotes implémentent.  
  
     Au lieu de cela, ODBC expose un nombre significatif de fonctionnalités (plus que celles prises en charge par la plupart des SGBD), mais nécessite des pilotes pour implémenter uniquement un sous-ensemble de ces fonctionnalités. Les pilotes implémentent les fonctionnalités restantes uniquement s’ils sont pris en charge par le SGBD sous-jacent ou s’ils choisissent de les émuler. Ainsi, les applications peuvent être écrites pour exploiter les fonctionnalités d’un seul SGBD comme exposé par le pilote pour ce SGBD, pour utiliser uniquement les fonctionnalités utilisées par tous les SGBD, ou pour vérifier la prise en charge d’une fonctionnalité particulière et réagir en conséquence.  
  
     Pour qu’une application puisse déterminer les fonctionnalités prises en charge par un pilote et un SGBD, ODBC fournit deux fonctions (**SQLGetInfo** et **SQLGetFunctions**) qui renvoient des informations générales sur les fonctionnalités des pilotes et des SGBD, ainsi qu’une liste des fonctions prises en charge par le pilote. ODBC définit également les niveaux de conformité de la grammaire API et SQL, qui spécifient de nombreuses fonctionnalités prises en charge par le pilote. Pour plus d’informations, consultez [niveaux de conformité](../../odbc/reference/develop-app/conformance-levels.md).  
  
     Il est important de se souvenir que ODBC définit une interface commune pour toutes les fonctionnalités qu’il expose. Pour cette raison, les applications contiennent du code spécifique aux fonctionnalités, et non du code propre au SGBD, et peuvent utiliser tous les pilotes qui exposent ces fonctionnalités. L’un des avantages est que les applications n’ont pas besoin d’être mises à jour lorsque les fonctionnalités prises en charge par un SGBD sont améliorées. au lieu de cela, lorsqu’un pilote mis à jour est installé, l’application utilise automatiquement les fonctionnalités, car son code est spécifique aux fonctionnalités, et non spécifique au pilote ou au SGBD.
