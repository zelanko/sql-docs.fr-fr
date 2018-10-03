---
title: La Solution ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30ced2aec9d7b91f5c3df55a7d6bf1f7e8a69d1c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47822557"
---
# <a name="the-odbc-solution"></a>La solution ODBC
Ensuite, la question est comment ODBC normaliser les accès de base de données ? Il existe deux spécifications architecturales :  
  
-   Applications doivent être en mesure d’accéder à l’aide du même code source sans devoir recompiler ni la réédition de liens de plusieurs systèmes SGBD.  
  
-   Applications doivent être en mesure d’accéder simultanément à plusieurs systèmes SGBD.  
  
 Et il est une question de plus, en raison de la réalité de la place de marché :  
  
-   Les fonctionnalités de SGBD doit exposer ODBC ? Uniquement les fonctionnalités qui sont communes à tous les SGBD ou toute fonctionnalité qui est disponible dans n’importe quel SGBD ?  
  
 ODBC résout ces problèmes de la manière suivante :  
  
-   **ODBC est une interface de niveau d’appel.** Pour résoudre le problème des applications comment accéder à plusieurs systèmes de SGBD à l’aide du même code source, ODBC définit une interface CLI standard. Ce fichier contient toutes les fonctions dans les spécifications de l’interface CLI à partir d’Open Group et ISO/IEC et fournit des fonctions supplémentaires couramment requises par les applications.  
  
     Une autre bibliothèque ou pilote, est requis pour chaque SGBD qui prend en charge ODBC. Le pilote implémente les fonctions de l’API ODBC. Pour utiliser un autre pilote, l’application est inutile d’être recompilées ni lié à nouveau. Au lieu de cela, l’application charge le nouveau pilote simplement et appelle les fonctions qu’elle contient. Pour accéder simultanément à plusieurs systèmes SGBD, l’application charge plusieurs pilotes. Comment les pilotes sont pris en charge est propre au système d’exploitation. Par exemple, sur le système d’exploitation Microsoft® Windows®, les pilotes sont des bibliothèques de liens dynamiques (DLL).  
  
-   **ODBC définit une syntaxe SQL standard.** Outre une interface de niveau d’appel standard, ODBC définit une syntaxe SQL standard. Cette syntaxe est basée sur la spécification Open IAO SQL de groupe. Différences entre les deux grammaires sont mineures et principalement en raison des différences entre la grammaire SQL requis par embedded SQL (Open Group) et une interface CLI (ODBC). Il existe également certaines extensions à la grammaire d’exposer les fonctionnalités de langage disponibles couramment non couvertes par la grammaire Open Group.  
  
     Les applications peuvent envoyer des instructions à l’aide de la grammaire ODBC ou propres au SGBD. Si une instruction utilise la grammaire ODBC qui diffère de la grammaire de SGBD spécifiques, le pilote convertit avant de les envoyer à la source de données. Toutefois, ces conversions sont rares, car la plupart des SGBD utilisent déjà la grammaire SQL standard.  
  
-   **ODBC fournit un gestionnaire de pilote pour gérer l’accès simultané à plusieurs systèmes SGBD.** Bien que l’utilisation de pilotes a résolu le problème d’accéder simultanément à plusieurs systèmes SGBD, le code d’implémentation peut être complexe. Les applications qui sont conçues pour fonctionner avec tous les pilotes ne peuvent pas être liées statiquement pour tous les pilotes. Au lieu de cela, ils doivent charger les pilotes en cours d’exécution et appeler les fonctions dans les via un tableau de pointeurs de fonction. La situation devient plus complexe si l’application utilise plusieurs pilotes simultanément.  
  
     Au lieu d’obliger chaque application pour ce faire, ODBC fournit un gestionnaire de pilotes. Le Gestionnaire de pilotes implémente toutes les fonctions ODBC — principalement comme des appels directs aux fonctions ODBC dans les pilotes et est statiquement lié à l’application ou chargée par l’application au moment de l’exécution. Par conséquent, l’application appelle les fonctions ODBC par nom dans le Gestionnaire de pilotes, plutôt que par pointeur dans chaque pilote.  
  
     Lorsqu’une application a besoin d’un pilote spécifique, il demande tout d’abord un handle de connexion permettant d’identifier le pilote, puis les demandes que le Gestionnaire de pilotes charger le pilote. Le Gestionnaire de pilotes charge le pilote et stocke l’adresse de chaque fonction dans le pilote. Pour appeler une fonction ODBC dans le pilote, l’application appelle cette fonction dans le Gestionnaire de pilotes et passe le handle de connexion pour le pilote. Le Gestionnaire de pilotes appelle ensuite la fonction à l’aide de l’adresse stockées précédemment.  
  
-   **ODBC expose un nombre important de fonctionnalités de SGBD, mais ne nécessite pas de pilotes pour prendre en charge tous les.** Si ODBC exposé uniquement les fonctionnalités qui sont communes à tous les SGBD, il serait peu utiles ; Après tout, afin de nombreux SGBD différents existe aujourd'hui parce qu’ils ont des fonctionnalités différentes. Si ODBC exposé toutes les fonctionnalités qui est disponible dans n’importe quel SGBD, il serait impossible pour les pilotes à mettre en œuvre.  
  
     Au lieu de cela, ODBC expose un nombre important de fonctionnalités, plus de sont pris en charge par la plupart des SGBD, mais nécessite des pilotes pour implémenter uniquement un sous-ensemble de ces fonctionnalités. Pilotes implémentent les fonctionnalités restantes uniquement si elles sont prises en charge par le SGBD sous-jacent ou s’ils choisissent d’émuler les. Par conséquent, les applications peuvent être écrites pour exploiter les fonctionnalités de SGBD unique comme exposé par le pilote pour ce système SGBD, à utiliser uniquement les fonctionnalités utilisées par tous les SGBD, ou pour vérifier la prise en charge d’une fonctionnalité particulière et réagir en conséquence.  
  
     Afin qu’une application peut déterminer quelles sont les fonctionnalités un pilote et SGBD prennent en charge, ODBC fournit deux fonctions (**SQLGetInfo** et **SQLGetFunctions**) qui retournent des informations générales sur le pilote et le SGBD le pilote prend en charge une liste de fonctions et de fonctionnalités. ODBC définit également des API et SQL grammaire niveaux de conformité, qui spécifient des plages large de fonctionnalités prises en charge par le pilote. Pour plus d’informations, consultez [niveaux de conformité](../../odbc/reference/develop-app/conformance-levels.md).  
  
     Il est important de se rappeler que ODBC définit une interface commune pour toutes les fonctionnalités qu’il expose. Pour cette raison, les applications contiennent du code spécifique à la fonctionnalité, pas de code propres au SGBD et peuvent utiliser des pilotes qui exposent ces fonctionnalités. Un avantage de ceci est que les applications n’avez pas besoin d’être mis à jour lorsque les fonctionnalités prises en charge par un SGBD sont améliorées ; au lieu de cela, lorsqu’un pilote mis à jour est installé, l’application utilise automatiquement les fonctionnalités, car son code est spécifique à la fonctionnalité, pas spécifiques au pilote ou un SGBD spécifiques.
