---
title: Définition des valeurs paramètres (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- parameter values [ODBC]
ms.assetid: 13e5da79-b60c-48d0-b467-773f481ef2a4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 923fd57f4308fb72aca2f829ccb9d7b884c12546
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299829"
---
# <a name="setting-parameter-values"></a>Définition de valeurs de paramètres
Pour définir la valeur d’un paramètre, l’application définit simplement la valeur de la variable liée au paramètre. Il n’est pas important lorsque cette valeur est définie, tant qu’elle est définie avant que la déclaration ne soit exécutée. L’application peut définir la valeur avant ou après la liaison de la variable, et elle peut changer la valeur autant de fois qu’elle le souhaite. Lorsque la déclaration est exécutée, le conducteur récupère simplement la valeur actuelle de la variable. Cela est particulièrement utile lorsqu’une déclaration préparée est exécutée plus d’une fois; l’application définit de nouvelles valeurs pour une partie ou la totalité des variables chaque fois que l’instruction est exécutée. Pour un exemple de cela, voir [l’exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md), plus tôt dans cette section.  
  
 Si un tampon de longueur/indicateur a été lié dans l’appel à **SQLBindParameter**, il doit être réglé à l’une des valeurs suivantes avant que la déclaration soit exécutée :  
  
-   La longueur d’en-avant des données dans la variable liée. Le conducteur ne vérifie cette longueur que si la variable est de caractère ou binaire *(ValueType* est SQL_C_CHAR ou SQL_C_BINARY).  
  
-   SQL_NTS. Les données sont une chaîne non terminée.  
  
-   SQL_NULL_DATA. La valeur de données est NULL, et le conducteur ignore la valeur de la variable liée.  
  
-   SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC. La valeur du paramètre doit être envoyée avec **SQLPutData**. Pour plus d’informations, voir [Envoyer des données longues](../../../odbc/reference/develop-app/sending-long-data.md), plus tard dans cette section.  
  
 Le tableau suivant montre les valeurs de la variable liée et le tampon longueur/indicateur que l’application fixe pour une variété de valeurs de paramètres.  
  
|Paramètre<br /><br /> value|Paramètre<br /><br /> (SQL)<br /><br /> type de données|Variable (C)<br /><br /> type de données|Valeur dans<br /><br /> lié<br /><br /> variable|Valeur dans<br /><br /> longueur/indicateur<br /><br /> tampon[d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|ABC-0[a]|SQL_NTS ou 3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|10 à 0[a]|SQL_NTS ou 2|  
|13 h|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13,0,0[b]|--|  
|13 h|SQL_TYPE_TIME|SQL_C_CHAR|T '13:00:00'0[a], [c]|SQL_NTS ou 14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a] « 0 » représente un caractère de résiliation nulle. Le caractère de résiliation nulle n’est requis que si la valeur du tampon longueur/indicateur est SQL_NTS.  
  
 [b] Les chiffres de cette liste sont les nombres stockés dans les champs de la structure TIME_STRUCT.  
  
 [c] La chaîne utilise la clause d’évasion de date de l’ODBC. Pour plus d’informations, voir [Date, Time, et Timestamp Literals](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 [d] Les conducteurs doivent toujours vérifier cette valeur pour voir s’il s’agit d’une valeur spéciale, comme SQL_NULL_DATA.  
  
 Ce qu’un conducteur fait avec une valeur de paramètre au moment de l’exécution dépend du conducteur. Si nécessaire, le conducteur convertit la valeur du type de données C et de la longueur des bytes de la variable liée au type de données SQL, à la précision et à l’échelle du paramètre. Dans la plupart des cas, le conducteur envoie ensuite la valeur à la source de données. Dans certains cas, il formate la valeur sous forme de texte et l’insère dans la déclaration SQL avant d’envoyer la déclaration à la source de données.
