---
title: 'SQL à C : intervalles d’un mois d’année Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba79a4d6165a43676634a6b79db56b88f5bcc234
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296389"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL à C : Intervalles d’années-mois

Les identificateurs pour l’intervalle de mois ODBC SQL types de données sont les suivants:

- SQL_INTERVAL_MONTH
- SQL_INTERVAL_YEAR
- SQL_INTERVAL_YEAR_TO_MONTH

Le tableau suivant montre les types de données ODBC C auxquels les données SQL d’intervalle d’un mois peuvent être converties. Pour une explication des colonnes et des termes dans le tableau, voir [convertir les données de SQL à C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  

|Identifiant de type C|Test|TargetValuePtr (en)|StrLen_or_IndPtr|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH[a]<br /><br /> SQL_C_INTERVAL_YEAR[a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH[a]|Partie des champs de trail non tronquée<br /><br /> Partie des champs de trail tronquée<br /><br /> La précision de pointe de la cible n’est pas assez grande pour contenir les données de la source|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT[b]<br /><br /> SQL_C_UTINYINT[b]<br /><br /> SQL_C_USHORT[b]<br /><br /> SQL_C_SHORT[b]<br /><br /> SQL_C_SLONG[b]<br /><br /> SQL_C_ULONG[b]<br /><br /> SQL_C_NUMERIC[b]<br /><br /> SQL_C_BIGINT[b]|La précision d’intervalle était un champ unique et les données ont été converties sans troncation<br /><br /> La précision d’intervalle était un champ simple et tronquée entière<br /><br /> La précision d’intervalle n’était pas un seul champ|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Longueur des données dans les octets<br /><br /> Taille du type de données C|n/a<br /><br /> 22003<br /><br /> 22015|  
|SQL_C_BINARY|Longueur d’enseille des données <*'BufferLength'*<br /><br /> Longueur d’enseille des données > *BufferLength*|Données<br /><br /> Indéfini|Longueur des données dans les octets<br /><br /> Indéfini|n/a<br /><br /> 22003|  
|SQL_C_CHAR|Longueur d’en-linge de caractère < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) >' *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|Longueur de caractère < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) < *BufferLength*<br /><br /> Nombre de chiffres entiers (par opposition à fractionnels) >' *BufferLength*|Données<br /><br /> Données tronquées<br /><br /> Indéfini|Taille du type de données C<br /><br /> Taille du type de données C<br /><br /> Indéfini|n/a<br /><br /> 01004<br /><br /> 22003|  
  
 [a] Un type SQL d’intervalle d’un mois d’année peut être converti en n’importe quel type d’intervalle C d’un mois d’année.  
  
 [b] Si la précision d’intervalle est un seul champ (un de l’ANNÉE ou de month), le type SQL d’intervalle peut être converti en n’importe quel numérique exact (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_USHORT, SQL_C_SHORT, SQL_C_SLONG, SQL_C_ULONG, ou SQL_C_NUMERIC).  

## <a name="default-conversions"></a>Conversions par défaut

La conversion par défaut d’un type SQL d’intervalle est au type de données d’intervalle C correspondant. L’application lie ensuite la colonne ou le paramètre (ou définit le champ SQL_DESC_DATA_PTR dans le dossier approprié de l’ARD) pour indiquer la structure SQL_INTERVAL_STRUCT initialisée (ou passe un pointeur à la structure INTERVAL_STRUCT SQL_ comme l’argument *TargetValuePtr* dans un appel à **SQLGetData**).
