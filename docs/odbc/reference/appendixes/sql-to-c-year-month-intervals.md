---
title: 'SQL à C : Intervalles d’années-mois | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01af57739f23db586991f8a54d14b90b47f15933
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259576"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL à C : Intervalles d’années-mois

Les identificateurs pour les types de données SQL ODBC intervalle année-mois sont les suivantes :

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

Le tableau suivant présente le ODBC C types de données à partir de quel mois-année intervalle de données SQL peut-être être convertie. Pour obtenir une explication des colonnes et des termes dans la table, consultez [conversion des données à partir de SQL pour les Types de données C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Identificateur de type C|Test|TargetValuePtr|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH[a]<br /><br /> SQL_C_INTERVAL_YEAR[a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH[a]|Portion de champs ne pas tronquée à droite<br /><br /> Portion de champs tronquée à droite<br /><br /> La précision de la cible de début n’est pas assez grande pour contenir les données à partir de la source|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b]<br /><br /> SQL_C_UTINYINT[b]<br /><br /> SQL_C_USHORT[b]<br /><br /> SQL_C_SHORT[b]<br /><br /> SQL_C_SLONG[b]<br /><br /> SQL_C_ULONG[b]<br /><br /> SQL_C_NUMERIC[b]<br /><br /> SQL_C_BIGINT[b]|Précision de l’intervalle a été un champ unique et les données ont été converties sans troncation<br /><br /> Précision de l’intervalle a été un seul champ et tronqué en entier<br /><br /> Précision de l’intervalle n’était pas un champ unique|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Longueur des données en octets<br /><br /> Taille du type de données C|n/a<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Longueur d’octet de données < = *BufferLength*<br /><br /> Longueur d’octet de données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données en octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_CHAR|Longueur d’octet de caractère < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) > = *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Longueur des caractères < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) < *BufferLength*<br /><br /> Nombre de chiffres de l’ensemble (par opposition aux fractions de seconde) > = *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
  
 [a] intervalle année-mois d’un type SQL peut être converti en n’importe quel type d’intervalle C année-mois.  
  
 [b] si la précision de l’intervalle est un champ unique (une année ou un mois), l’intervalle de type SQL peut être converti en n’importe quel numérique exact (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG ou SQL_C_NUMERIC).  

## <a name="default-conversions"></a>Conversions par défaut

La conversion par défaut d’un intervalle de type SQL consiste au type de données d’intervalle C correspondant. L’application puis lie la colonne ou du paramètre (ou définit le champ SQL_DESC_DATA_PTR dans l’enregistrement approprié de la ARD) pour pointer vers la structure SQL_INTERVAL_STRUCT initialisée (ou passe un pointeur vers la structure SQL_ INTERVAL_STRUCT comme le *TargetValuePtr* argument dans un appel à **SQLGetData**).
