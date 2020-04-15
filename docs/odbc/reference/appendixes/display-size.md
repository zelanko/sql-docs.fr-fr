---
title: Taille de l’affichage (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- SQL data types [ODBC], column characteristics
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578bf0cbdf2dd1dbd06dd4a248f4efa5eb839916
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307030"
---
# <a name="display-size"></a>Taille d’affichage
La taille d’affichage d’une colonne est le nombre maximum de caractères nécessaires pour afficher les données sous forme de caractère. Le tableau suivant définit la taille de l’affichage pour chaque type de données SQL ODBC.  
  
|Identifiant de type SQL|Taille de l’écran|  
|-------------------------|------------------|  
|Tous les types de personnages[a]|Le nombre défini (pour les types fixes) ou le nombre maximum (pour les types variables) des caractères nécessaires pour afficher les données sous forme de caractère.|  
|SQL_DECIMAL SQL_NUMERIC|La précision de la colonne plus 2 (un signe, des chiffres de *précision,* et un point décimal). Par exemple, la taille d’affichage d’une colonne définie comme NUMERIC(10,3) est de 12.|  
|SQL_BIT|1 (1 chiffre).|  
|SQL_TINYINT|4 si signé (un signe et 3 chiffres) ou 3 si non signé (3 chiffres).|  
|SQL_SMALLINT|6 si signé (un signe et 5 chiffres) ou 5 si non signé (5 chiffres).|  
|SQL_INTEGER|11 si signé (un signe et 10 chiffres) ou 10 si non signé (10 chiffres).|  
|SQL_BIGINT|20 (un signe et 19 chiffres s’ils sont signés ou 20 chiffres s’ils ne sont pas signés).|  
|SQL_REAL|14 (un signe, 7 chiffres, un point décimal, la lettre *E*, un signe, et 2 chiffres).|  
|SQL_FLOAT SQL_DOUBLE|24 (un signe, 15 chiffres, un point décimal, la lettre *E*, un signe, et 3 chiffres).|  
|Tous les types binaires[a]|La longueur définie ou maximale (pour les types variables) de la colonne fois 2. (Chaque byte binaire est représenté par un nombre hexadecimal à 2 chiffres.)|  
|SQL_TYPE_DATE|10 (une date dans le format *yyyy-mm-dd*).|  
|SQL_TYPE_TIME|8 (un temps dans le format *hh:mm:ss*)<br /><br /> - ou -<br /><br /> 9 *s* (un temps dans le format *hh:mm:ss*[.fff...], où *s* est la précision fractionnelle secondes).|  
|SQL_TYPE_TIMESTAMP|19 (pour un timestamp dans le *yyyy-mm-dd hh:mm:ss* format)<br /><br /> - ou -<br /><br /> 20 *s* (pour un horodatage dans le *yyyy-mm-dd hh:mm:ss*[.fff...] format, où *s* est la précision fractionnelle secondes).|  
|Tous les types de données d’intervalle|Voir [Interval Data Type Length](../../../odbc/reference/appendixes/interval-data-type-length.md).|  
|SQL_GUID|36 (le nombre de caractères dans le format *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeeeeee*|  
  
 [a] Si le conducteur ne peut pas déterminer la longueur de colonne ou de paramètre des types variables, il retourne SQL_NO_TOTAL.
