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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063354"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Niveaux de conformité de SQL (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge la grammaire SQL minimale et la grammaire SQL principale et prend également en charge les extensions SQL ODBC suivantes :  
  
-   Données de date, time et timestamp  
  
-   Les jointures externes droite et gauche  
  
-   Fonctions numériques :  
  
    |||||  
    |-|-|-|-|  
    |Abs|Journal|round|tan|  
    |plafond|LOG10|second|truncate|  
    |Cos|Mod|connexion||  
    |Exp|PI|sin||  
    |Floor|Power|sqrt||  
  
-   Fonctions de date :  
  
    |||||  
    |-|-|-|-|  
    |CURDATE|DayOfWeek|MonthName|second|  
    |Curtime|Jour de l'année|minute|week|  
    |DAYNAME|Heure|now|year|  
    |DayOfMonth|Mois|Trimestre||  
  
-   Fonctions de chaîne :  
  
    |||||  
    |-|-|-|-|  
    |ASCII|Gauche|Oui|UCase|  
    |Char|Longueur|RTrim||  
    |Concat|LTrim|SOUNDEX||  
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
