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
ms.openlocfilehash: 969296e377d398615ad95cf1337c3f9f97d5eb5c
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363399"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Niveaux de conformité de SQL (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge la grammaire SQL minimale et la grammaire SQL de base, et prend également en charge les extensions ODBC suivantes pour SQL :  
  
-   Données de date, d’heure et d’horodatage  
  
-   Jointures externes gauches et droites  
  
-   Fonctions numériques :  

    :::row:::
        :::column:::
            Abs  
            Ceiling  
            Cos  
            Exp  
            Floor  
        :::column-end:::
        :::column:::
            Journal  
            Log10  
            Mod  
            Pi  
            Power  
        :::column-end:::
        :::column:::
            round  
            second  
            sign  
            sin  
            sqrt  
        :::column-end:::
        :::column:::
            tan  
            truncate  
        :::column-end:::
    :::row-end:::
    
-   Fonctions de date :  

    :::row:::
        :::column:::
            CURDATE  
            Curtime  
            Dayname  
            DayOfMonth  
        :::column-end:::
        :::column:::
            DayOfWeek  
            Jour de l'année  
            Heure  
            Month  
        :::column-end:::
        :::column:::
            MonthName  
            minute  
            now  
            quarter  
        :::column-end:::
        :::column:::
            second  
            week  
            year  
        :::column-end:::
    :::row-end:::

-   Fonctions de chaînes :  

    :::row:::
        :::column:::
            ASCII  
            Char  
            Concat  
            Lcase  
        :::column-end:::
        :::column:::
            Gauche  
            Longueur  
            LTRIM  
            Replace  
        :::column-end:::
        :::column:::
            droite  
            RTrim  
            Soundex  
            substring  
        :::column-end:::
        :::column:::
            UCase  
        :::column-end:::
    :::row-end:::

-   Fonction de conversion de type :  

    Convertir  

-   Fonctions système :  
  
    Ifnull  
    Utilisateur
