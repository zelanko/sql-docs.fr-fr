---
title: Types de données de date/heure | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d546fff544c616d4f2750dba76c4b8e68d21aab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619520"
---
# <a name="datetime-data-types"></a>Type de données datetime
Dans ODBC 3 *.x*, les identificateurs de date, heure et types de données timestamp SQL ont été modifiés à partir de SQL_DATE, SQL_TIME et SQL_TIMESTAMP (avec des instances de **#define** dans le fichier d’en-tête de 9, 10 et 11) à SQL_ TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP (avec des instances de **#define** dans le fichier d’en-tête de 91, 92 et 93), respectivement. Le type C correspondant identificateurs ont été modifiés à partir de SQL_C_DATE, SQL_C_TIME et SQL_C_TIMESTAMP SQL_C_TYPE_DATE SQL_C_TYPE_TIME et SQL_C_TYPE_TIMESTAMP, respectivement et les instances de **#define** ont été modifiés en conséquence.  
  
 La taille de colonne et les chiffres décimaux retournaient pour les types de données datetime SQL dans ODBC 3 *.x* sont le même que la précision et l’échelle retourné pour eux dans ODBC 2. *x*. Ces valeurs sont différentes de celles figurant dans les champs de descripteur SQL_DESC_PRECISION et SQL_DESC_SCALE. (Pour plus d’informations, consultez [taille de colonne, des chiffres décimaux, transférer la longueur en octets et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) annexe d : Types de données.)  
  
 Ces modifications affectent **SQLDescribeCol**, **SQLDescribeParam**, et **SQLColAttributes**; **SQLBindCol**, **SQLBindParameter**, et **SQLGetData**; et **SQLColumns**, **SQLGetTypeInfo** , **SQLProcedureColumns**, **SQLStatistics**, et **SQLSpecialColumns**.  
  
 Un ODBC 3 *.x* pilote traite les appels de fonction répertoriés dans le paragraphe précédent en fonction du paramètre de l’attribut d’environnement SQL_ATTR_ODBC_VERSION. Pour **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, **SQLSpecialColumns**, et **SQLStatistics** , si SQL_ATTR_ODBC_VERSION est défini à SQL_OV_ODBC3, les fonctions retour SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP dans le champ DATA_TYPE. La colonne COLUMN_SIZE (dans le jeu de résultats retourné par **SQLColumns**, **SQLGetTypeInfo**, **SQLProcedureColumns**, et **SQLSpecialColumns**) contient la précision binaire pour le type numérique approximatif. La colonne NUM_PREC_RADIX (dans le jeu de résultats retourné par **SQLColumns**, **SQLGetTypeInfo**, et **SQLProcedureColumns**) contient une valeur de 2. Si SQL_ATTR_ODBC_VERSION est définie sur SQL_OV_ODBC2, les fonctions retour SQL_DATE, SQL_TIME et SQL_TIMESTAMP dans le champ DATA_TYPE, la colonne COLUMN_SIZE contient la précision décimale pour le type numérique approximatif et que la colonne NUM_PREC_RADIX contient une valeur de 10.  
  
 Lorsque tous les types de données sont demandées dans un appel à **SQLGetTypeInfo**, le jeu de résultats retourné par la fonction contient à la fois SQL_TYPE_DATE, SQL_TYPE_TIME et SQL_TYPE_TIMESTAMP tel que défini dans ODBC 3 *.x*, et SQL_DATE, SQL_TIME et SQL_TIMESTAMP tel que défini dans ODBC 2. *x*.  
  
 En raison de la façon la ODBC 3 *.x* Gestionnaire de pilotes effectue un mappage des types de données date, time et timestamp, ODBC 3 *.x* pilotes suffit de reconnaître **#defines** 91, 92, et 93 pour la date, heure et types de données timestamp C est entré dans le *TargetType* arguments de **SQLBindCol** et **SQLGetData** ou  *ValueType* argument de **SQLBindParameter**et vous suffit de reconnaître **#defines** 91, 92 et 93 pour la date, heure et types de données timestamp SQL entré dans le *ParameterType* argument de **SQLBindParameter** ou *DataType* argument de **SQLGetTypeInfo**. Pour plus d’informations, consultez [modifications de Type de données Datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md).
