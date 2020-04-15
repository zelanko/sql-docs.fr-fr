---
title: Types de données date d’heure de date Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- data types [ODBC], date
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- data types [ODBC], timestamp
- data types [ODBC], backward compatibility
- compatibility [ODBC], datetime data types
- data types [ODBC], time
ms.assetid: 6b9363c9-04bf-4492-a210-7aa15dea4af8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10626c4f0bf2e33c70322a0eb49af6c3e01e4303
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307060"
---
# <a name="datetime-data-types"></a>Type de données datetime
Dans ODBC *3.x*, les identificateurs pour la date, les types de données SQL de temps, et de temps en retard sont passés de SQL_DATE, SQL_TIME et SQL_TIMESTAMP (avec des cas de **#define** dans le fichier d’en-tête de 9, 10 et 11) à SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP (avec des cas de **#define** dans le fichier d’en-tête de 91, 92 et 93), respectivement. Les identificateurs de type C correspondants sont passés de SQL_C_DATE, SQL_C_TIME et SQL_C_TIMESTAMP à SQL_C_TYPE_DATE, SQL_C_TYPE_TIME et SQL_C_TYPE_TIMESTAMP, respectivement, et les cas de **#define** ont changé en conséquence.  
  
 La taille de la colonne et les chiffres décimaux retournés pour les types de données SQL datetime dans ODBC *3.x* sont les mêmes que la précision et l’échelle retournée pour eux dans ODBC *2.x*. Ces valeurs sont différentes des valeurs des champs de SQL_DESC_PRECISION et de SQL_DESC_SCALE descripteur. (Pour plus d’informations, voir [Taille de colonne, chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.)  
  
 Ces changements affectent **SQLDescribeCol**, **SQLDescribeParam**, et **SQLColAttributes**; **SQLBindCol**, **SQLBindParameter**, et **SQLGetData**; et **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLStatistics**, et **SQLSpecialColumns**.  
  
 Un pilote ODBC *3.x* traite les appels de fonction énumérés dans le paragraphe précédent en fonction du paramètre de l’attribut SQL_ATTR_ODBC_VERSION environnement. Pour **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLSpecialColumns**, et **SQLStatistics**, si SQL_ATTR_ODBC_VERSION est mis à SQL_OV_ODBC3, les fonctions reviennent SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP dans le domaine DATA_TYPE. La colonne COLUMN_SIZE (dans l’ensemble de résultats retournés par **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, et **SQLSpecialColumns**) contient la précision binaire pour le type numérique approximatif. La colonne NUM_PREC_RADIX (dans l’ensemble de résultats retournés par **SQLColumns**, **SQLGetTypeInfo**, et **SQLProcedureColumns**) contient une valeur de 2. Si SQL_ATTR_ODBC_VERSION est réglée pour SQL_OV_ODBC2, alors les fonctions retournent SQL_DATE, SQL_TIME et SQL_TIMESTAMP dans le champ DATA_TYPE, la colonne COLUMN_SIZE contient la précision décimale pour le type numérique approximatif, et la colonne NUM_PREC_RADIX contient une valeur de 10.  
  
 Lorsque tous les types de données sont demandés dans un appel à **SQLGetTypeInfo**, le résultat établi par la fonction contiendra à la fois SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP tel que défini dans ODBC *3.x*, et SQL_DATE, SQL_TIME, et SQL_TIMESTAMP tel que défini dans ODBC *2.x*.  
  
 En raison de la façon dont l’ODBC *3.x* Driver Manager effectue la cartographie des types de données de la date, de l’heure et de l’humidité du temps, les conducteurs d’ODBC *3.x* n’ont besoin que de reconnaître **#defines** de 91, 92 et 93 pour la date, l’heure, et les types de données timetamp C entrés dans les arguments *TargetType* de **SQLBindCol** et **SQLGetData** ou *l’argument ValueType* de **SQLBindParameter**, et n’ont qu’à reconnaître **#defines** de 91, 92 et 93 pour la date, l’heure et les types de données SQLamp entrés dans *l’argument De ParameterType* de **SQLBindParameter** ou *l’argument DataType* de **SQGetY .** Pour plus d’informations, voir [Variations de type de données Datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md).
