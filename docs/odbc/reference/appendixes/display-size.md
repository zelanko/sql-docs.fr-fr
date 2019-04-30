---
title: Taille d’affichage | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c7d4a14a6afc2d716e85e687cbae1a202a596d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241252"
---
# <a name="display-size"></a>Taille d’affichage
La taille d’affichage d’une colonne est le nombre maximal de caractères que nécessaire pour afficher les données sous forme de caractère. Le tableau suivant définit la taille d’affichage pour chaque type de données ODBC SQL.  
  
|Identificateur de type SQL|Taille d’affichage|  
|-------------------------|------------------|  
|Tous les types de caractères [a]|Défini (pour les types fixes) ou maximum (pour les types de variables) nombre de caractères nécessaires pour afficher les données sous forme de caractère.|  
|SQL_DECIMAL SQL_NUMERIC|La précision de la colonne plus 2 (un signe, *précision* , des chiffres et une virgule décimale). Par exemple, la taille d’affichage d’une colonne définie en tant que NUMERIC(10,3) est 12.|  
|SQL_BIT|1 (1 chiffre).|  
|SQL_TINYINT|4 si connecté (un signe et 3 chiffres) ou 3 si non signé (3 chiffres).|  
|SQL_SMALLINT|6 si connecté (un signe et 5 chiffres) ou 5 si non signé (5 chiffres).|  
|SQL_INTEGER|11 si connecté (un signe et 10 chiffres) ou 10 si non signé (10 chiffres).|  
|SQL_BIGINT|20 (un signe et 19 si connecté ou 20 chiffres si non signé).|  
|SQL_REAL|14 (une connexion, 7 chiffres, une virgule décimale, la lettre *E*, un signe et 2 chiffres).|  
|SQL_FLOAT SQL_DOUBLE|24 (un signe, 15 chiffres, une virgule décimale, la lettre *E*, une connexion, ainsi que 3 chiffres).|  
|Tous les types binaires [a]|Défini ou maximum (pour les types de variables) longueur de la colonne 2 de fois. (Chaque octet binaire est représentée par un nombre hexadécimal à 2 chiffres).|  
|SQL_TYPE_DATE|10 (une date au format *aaaa-mm-jj*).|  
|SQL_TYPE_TIME|8 (une heure au format *hh : mm :*)<br /><br /> - ou -<br /><br /> 9 + *s* (une heure au format *hh : mm :*[.fff...], où *s* est la précision en fractions de seconde).|  
|SQL_TYPE_TIMESTAMP|19 (pour un horodatage dans le *aaaa-mm-jj hh : mm :* format)<br /><br /> - ou -<br /><br /> 20 + *s* (pour un horodatage dans le *aaaa-mm-jj hh : mm :* format [.fff...], où *s* est la précision en fractions de seconde).|  
|Tous les types de données d’intervalle|Consultez [longueur du Type de données de l’intervalle](../../../odbc/reference/appendixes/interval-data-type-length.md).|  
|SQL_GUID|36 (le nombre de caractères dans le *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* format|  
  
 [a] si le pilote ne peut pas déterminer la longueur de colonne ou du paramètre des types de variables, elle retourne SQL_NO_TOTAL.
