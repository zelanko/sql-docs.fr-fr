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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 241f4f3da12f63c15d917a0e47cb13ad0e96e6e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063354"
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
    |Floor|Puissance|sqrt||  
  
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
    |ASCII|Gauche|Oui|UCase|  
    |Char|Longueur|RTrim||  
    |Concat|LTRIM|Soundex||  
    |LCase|Replace|substring||  
  
-   Fonction de conversion de type :  
  
    ||  
    |-|  
    |Convertir|  
  
-   Fonctions système :  
  
    ||  
    |-|  
    |Ifnull|  
    |Utilisateur|
