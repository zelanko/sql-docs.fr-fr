---
title: La solution ODBC (fr) Microsoft Docs
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
ms.openlocfilehash: 2b35883ff4d621f0ecc092020ad744455281dd63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286752"
---
# <a name="the-odbc-solution"></a>La solution ODBC
La question est donc de savoir comment ODBC normalise l’accès aux bases de données? Il y a deux exigences architecturales :  
  
-   Les applications doivent être en mesure d’accéder à plusieurs DBMS en utilisant le même code source sans se recompiler ou reconnecter.  
  
-   Les applications doivent être en mesure d’accéder simultanément à plusieurs DBMS.  
  
 Et il ya une question de plus, en raison de la réalité du marché:  
  
-   Quelles fonctionnalités DBMS ODBC devraient-elles exposer? Seules les fonctionnalités qui sont communes à tous les DBMS ou toute fonctionnalité qui est disponible dans n’importe quel DBMS?  
  
 ODBC résout ces problèmes de la manière suivante :  
  
-   **ODBC est une interface de niveau d’appel.** Pour résoudre le problème de la façon dont les applications accèdent à plusieurs DBMS à l’aide du même code source, ODBC définit un CLI standard. Cela contient toutes les fonctions dans les spécifications CLI de Open Group et ISO/IEC et fournit des fonctions supplémentaires couramment requises par les applications.  
  
     Une bibliothèque ou un conducteur différent est nécessaire pour chaque DBMS qui prend en charge ODBC. Le conducteur implémente les fonctions dans l’API ODBC. Pour utiliser un autre pilote, l’application n’a pas besoin d’être recompilée ou reconnectée. Au lieu de cela, l’application charge simplement le nouveau pilote et appelle les fonctions en elle. Pour accéder simultanément à plusieurs DBMS, l’application charge plusieurs pilotes. La façon dont les conducteurs sont pris en charge est spécifique au système d’exploitation. Par exemple, sur le système d’exploitation Microsoft® Windows®, les pilotes sont des bibliothèques à liaison dynamique (DLL).  
  
-   **ODBC définit une grammaire SQL standard.** En plus d’une interface standard au niveau des appels, ODBC définit une grammaire SQL standard. Cette grammaire est basée sur les spécifications CAE open Group SQL. Les différences entre les deux grammaires sont mineures et principalement en raison des différences entre la grammaire SQL requise par SQL intégré (Groupe ouvert) et un CLI (ODBC). Il ya aussi quelques extensions à la grammaire pour exposer les caractéristiques linguistiques couramment disponibles non couvertes par la grammaire Open Group.  
  
     Les demandes peuvent soumettre des relevés à l’aide de la grammaire spécifique à l’ODBC ou au DBMS. Si une instruction utilise la grammaire ODBC qui est différente de la grammaire spécifique À DBMS, le pilote la convertit avant de l’envoyer à la source de données. Cependant, de telles conversions sont rares parce que la plupart des DBMS utilisent déjà la grammaire SQL standard.  
  
-   **ODBC fournit un gestionnaire de chauffeur pour gérer l’accès simultané à plusieurs DBMS.** Bien que l’utilisation de pilotes résout le problème de l’accès à plusieurs DBMS simultanément, le code pour ce faire peut être complexe. Les applications conçues pour fonctionner avec tous les conducteurs ne peuvent pas être statiquement liées à des pilotes. Au lieu de cela, ils doivent charger les pilotes au moment de la course et appeler les fonctions en eux à travers un tableau de pointeurs de fonction. La situation devient plus complexe si l’application utilise plusieurs pilotes simultanément.  
  
     Plutôt que de forcer chaque application à le faire, ODBC fournit un gestionnaire de conducteur. Le Gestionnaire de conducteur met en œuvre toutes les fonctions ODBC - principalement sous forme d’appels de passage vers les fonctions ODBC dans les pilotes - et est statiquement lié à l’application ou chargé par l’application au moment de l’exécution. Ainsi, l’application appelle les fonctions ODBC par leur nom dans le gestionnaire de conducteur, plutôt que par pointeur dans chaque pilote.  
  
     Lorsqu’une application a besoin d’un conducteur particulier, elle demande d’abord une poignée de connexion pour identifier le conducteur, puis demande au gestionnaire de conducteur de charger le conducteur. Le gestionnaire de conducteur charge le conducteur et stocke l’adresse de chaque fonction dans le conducteur. Pour appeler une fonction ODBC dans le conducteur, l’application appelle cette fonction dans le gestionnaire de conducteur et passe la poignée de connexion pour le conducteur. Le Gestionnaire de pilote appelle ensuite la fonction en utilisant l’adresse qu’elle a stockée plus tôt.  
  
-   **ODBC expose un nombre important de fonctionnalités DBMS, mais n’exige pas des conducteurs qu’ils prennent en charge tous.** Si ODBC n’exposait que les caractéristiques qui sont communes à tous les DBMS, elle serait peu utile; après tout, la raison pour laquelle tant de DBMS différents existent aujourd’hui, c’est qu’ils ont des caractéristiques différentes. Si ODBC exposait toutes les fonctionnalités disponibles dans n’importe quel DBMS, il serait impossible pour les conducteurs de mettre en œuvre.  
  
     Au lieu de cela, ODBC expose un nombre important de fonctionnalités - plus que sont prises en charge par la plupart des DBMS - mais exige des pilotes de mettre en œuvre seulement un sous-ensemble de ces fonctionnalités. Les conducteurs implémentent les fonctionnalités restantes uniquement s’ils sont pris en charge par le DBMS sous-jacent ou s’ils choisissent de les imiter. Ainsi, les applications peuvent être écrites pour exploiter les caractéristiques d’un seul DBMS tel qu’exposé par le conducteur pour ce DBMS, pour n’utiliser que les fonctionnalités utilisées par tous les DBMS, ou pour vérifier le soutien d’une fonctionnalité particulière et réagir en conséquence.  
  
     Afin qu’une application puisse déterminer quelles sont les caractéristiques d’un soutien conducteur et DBMS, ODBC fournit deux fonctions (**SQLGetInfo** et **SQLGetFunctions**) qui renvoient des informations générales sur le conducteur et les capacités DBMS et une liste des fonctions que le conducteur prend en charge. ODBC définit également les niveaux de conformité à la grammaire API et SQL, qui spécifient de larges gammes de caractéristiques prises en charge par le conducteur. Pour plus d’informations, voir [Niveaux de conformité](../../odbc/reference/develop-app/conformance-levels.md).  
  
     Il est important de se rappeler qu’ODBC définit une interface commune pour toutes les fonctionnalités qu’elle expose. Pour cette raison, les applications contiennent du code spécifique aux fonctionnalités, et non un code spécifique à DBMS, et peuvent utiliser tous les pilotes qui exposent ces fonctionnalités. Un avantage de ceci est que les applications n’ont pas besoin d’être mises à jour lorsque les fonctionnalités prises en charge par un DBMS sont améliorées ; au lieu de cela, lorsqu’un pilote mis à jour est installé, l’application utilise automatiquement les fonctionnalités parce que son code est spécifique aux fonctionnalités, et non spécifique au conducteur ou spécifique à DBMS.
