---
title: Niveaux de conformité SQL (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e283bbc13f0d0dda055b047b027f7b9816502df5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300679"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Niveaux de conformité de SQL (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge la grammaire SQL minimale et la grammaire SQL de base, et prend également en charge les extensions ODBC suivantes pour SQL :  
  
-   Données de date, d’heure et d’horodatage  
  
-   Jointures externes gauches et droites  
  
-   Fonctions numériques :  
  
    |||||  
    |-|-|-|-|  
    |Abs|Journal|round|tan|  
    |Ceiling|Log10|second|truncate|  
    |Cos|Mod|sign||  
    |Exp|Pi|sin||  
    |Floor|Avancé|sqrt||  
  
-   Fonctions de date :  
  
    |||||  
    |-|-|-|-|  
    |CURDATE|DayOfWeek|MonthName|second|  
    |Curtime|Jour de l'année|minute|week|  
    |Dayname|Heure|now|year|  
    |DayOfMonth|Month|quarter||  
  
-   Fonctions de chaînes :  
  
    |||||  
    |-|-|-|-|  
    |ASCII|Gauche|droite|UCase|  
    |Char|Longueur|RTrim||  
    |Concat|LTRIM|Soundex||  
    |Lcase|Replace|substring||  
  
-   Fonction de conversion de type :  
  
    ||  
    |-|  
    |Convertir|  
  
-   Fonctions système :  
  
    ||  
    |-|  
    |Ifnull|  
    |Utilisateur|
