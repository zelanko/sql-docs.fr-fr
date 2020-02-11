---
title: Définition des valeurs des paramètres | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0bb1115290f53c19fae1aacb0a976cfcef63e086
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094234"
---
# <a name="setting-parameter-values"></a>Définition de valeurs de paramètres
Pour définir la valeur d’un paramètre, l’application définit simplement la valeur de la variable liée au paramètre. Elle n’est pas importante lorsque cette valeur est définie, à condition qu’elle soit définie avant l’exécution de l’instruction. L’application peut définir la valeur avant ou après la liaison de la variable, et elle peut modifier la valeur autant de fois qu’elle le souhaite. Lorsque l’instruction est exécutée, le pilote récupère simplement la valeur actuelle de la variable. Cela s’avère particulièrement utile quand une instruction préparée est exécutée plusieurs fois. l’application définit de nouvelles valeurs pour une partie ou l’ensemble des variables chaque fois que l’instruction est exécutée. Pour obtenir un exemple, consultez [Exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md), plus haut dans cette section.  
  
 Si une mémoire tampon de longueur/d’indicateur était liée dans l’appel à **SQLBindParameter**, elle doit être définie sur l’une des valeurs suivantes avant l’exécution de l’instruction :  
  
-   Longueur en octets des données dans la variable liée. Le pilote vérifie cette longueur uniquement si la variable est de type character ou Binary (*ValueType* est SQL_C_CHAR ou SQL_C_BINARY).  
  
-   SQL_NTS. Les données sont une chaîne terminée par le caractère null.  
  
-   SQL_NULL_DATA. La valeur des données est NULL et le pilote ignore la valeur de la variable liée.  
  
-   SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC. La valeur du paramètre doit être envoyée avec **SQLPutData**. Pour plus d’informations, consultez [envoi de données de type long](../../../odbc/reference/develop-app/sending-long-data.md), plus loin dans cette section.  
  
 Le tableau suivant montre les valeurs de la variable liée et la mémoire tampon de longueur/d’indicateur que l’application définit pour une variété de valeurs de paramètres.  
  
|Paramètre<br /><br /> value|Paramètre<br /><br /> Server<br /><br /> type de données|Variable (C)<br /><br /> type de données|Valeur dans<br /><br /> lié<br /><br /> variable|Valeur dans<br /><br /> longueur/indicateur<br /><br /> mémoire tampon [d]|  
|-------------------------|-----------------------------------------|----------------------------------|-------------------------------------|----------------------------------------------------|  
|"ABC"|SQL_CHAR|SQL_C_CHAR|ABC\0 [a]|SQL_NTS ou 3|  
|10|SQL_INTEGER|SQL_C_SLONG|10|--|  
|10|SQL_INTEGER|SQL_C_CHAR|10 \ 0 [a]|SQL_NTS ou 2|  
|1 H 00|SQL_TYPE_TIME|SQL_C_TYPE_TIME|13, 0, 0 [b]|--|  
|1 H 00|SQL_TYPE_TIME|SQL_C_CHAR|{t' 13:00:00 '} \ 0 [a], [c]|SQL_NTS ou 14|  
|NULL|SQL_SMALLINT|SQL_C_SSHORT|--|SQL_NULL_DATA|  
  
 [a] « \ 0 » représente un caractère de fin null. Le caractère de fin null est requis uniquement si la valeur de la mémoire tampon de longueur/d’indicateur est SQL_NTS.  
  
 [b] les nombres de cette liste sont les nombres stockés dans les champs de la structure TIME_STRUCT.  
  
 [c] la chaîne utilise la clause ODBC date Escape. Pour plus d’informations, consultez [littéraux de date, d’heure et d’horodatage](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 [d] les pilotes doivent toujours vérifier cette valeur pour voir s’il s’agit d’une valeur spéciale, par exemple SQL_NULL_DATA.  
  
 Le fonctionnement d’un pilote avec une valeur de paramètre au moment de l’exécution dépend du pilote. Si nécessaire, le pilote convertit la valeur du type de données C et la longueur en octets de la variable liée au type de données SQL, à la précision et à l’échelle du paramètre. Dans la plupart des cas, le pilote envoie la valeur à la source de données. Dans certains cas, il met en forme la valeur en tant que texte et l’insère dans l’instruction SQL avant d’envoyer l’instruction à la source de données.
