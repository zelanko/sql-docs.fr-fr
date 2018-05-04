---
title: Niveaux de conformité SQL (le pilote ODBC pour Oracle) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 247009b387cf7538a841477bab5f7be72fa20fd5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Niveaux de conformité SQL (le pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge la grammaire SQL minimale et la grammaire SQL principale et prend également en charge les extensions ODBC SQL suivantes :  
  
-   Données de date, time et timestamp  
  
-   Jointures externes droite et gauche  
  
-   Fonctions numériques :  
  
    |||||  
    |-|-|-|-|  
    |Abs|Journal|round|tan|  
    |Plafond|LOG10|second|truncate|  
    |Cos|Mod|Connexion||  
    |Exp|PI|sin||  
    |Floor|Power|SQRT||  
  
-   Fonctions de date :  
  
    |||||  
    |-|-|-|-|  
    |CURDATE|DayOfWeek|MonthName|second|  
    |Curtime|Jour de l'année|minute|week|  
    |HeureDAYNAME|Heure|maintenant|year|  
    |DayOfMonth|Mois|trimestre||  
  
-   Fonctions de chaîne :  
  
    |||||  
    |-|-|-|-|  
    |ASCII|Gauche|Oui|UCase|  
    |Char|Longueur|la fonction RTrim||  
    |Concat|La fonction LTrim|SOUNDEX||  
    |LCase|Remplacer|substring||  
  
-   Fonction de conversion de type :  
  
    ||  
    |-|  
    |Convertir|  
  
-   Fonctions système :  
  
    ||  
    |-|  
    |IFNULL|  
    |Utilisateur|
