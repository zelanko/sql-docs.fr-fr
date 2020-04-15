---
title: Transfert Octet Longueur (fr) Microsoft Docs
ms.custom: ''
ms.date: 10/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- SQL data types [ODBC], column characteristics
- data types [ODBC], transfer octet length
ms.assetid: 9fdc9762-e203-4cff-9212-54f450bf18d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4204b47816747506a5672241eeeef736eca54856
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302810"
---
# <a name="transfer-octet-length"></a>Longueur en octets du transfert
La longueur de l’octet de transfert d’une colonne est le nombre maximum d’octets retournés à l’application lorsque les données sont transférées à son type de données C par défaut. Pour les données de caractère, la longueur de l’octet de transfert n’inclut pas d’espace pour le caractère de non-terminaison. La longueur de l’octet de transfert d’une colonne peut être différente du nombre d’octets requis pour stocker les données sur la source de données.  
  
 La longueur de l’octet de transfert définie pour chaque type de données ODBC SQL est indiquée dans le tableau suivant.  
  
|Identifiant de type SQL|Longueur|  
|-------------------------|------------|  
|Tous les types de personnages[a]|La longueur définie ou maximale (pour type variable) de la colonne dans les octets. C’est la même valeur que le champ descripteur SQL_DESC_OCTET_LENGTH.|  
|SQL_DECIMAL<br />SQL_NUMERIC|Nombre d’octets requis pour conserver la représentation des caractères de ces données si l’ensemble de caractères est ANSI, et deux fois ce nombre si l’ensemble de caractères est UNICODE. Il s’agit du nombre maximum de chiffres plus deux, parce que les données sont retournées comme une chaîne de caractères et les caractères sont nécessaires pour les chiffres, un signe, et un point décimal. Par exemple, la durée de transfert d’une colonne définie comme NUMERIC(10,3) est de 12.|  
|SQL_TINYINT|1|  
|SQL_SMALLINT|2|  
|SQL_INTEGER|4|  
|SQL_BIGINT| 8 |  
|SQL_REAL|4|  
|SQL_FLOAT|8|  
|SQL_DOUBLE|8|  
|SQL_BIT|1|  
|Tous les types binaires[a]|Nombre d’octets requis pour contenir le nombre défini (pour les types fixes) ou maximum (pour les types variables).|  
|SQL_TYPE_DATE<br />SQL_TYPE_TIME|6 (la taille de la structure SQL_DATE_STRUCT ou SQL_TIME_STRUCT).|  
|SQL_TYPE_TIMESTAMP|16 (la taille de la structure SQL_TIMESTAMP_STRUCT).|  
|Tous les types de données d’intervalle|34 (la taille de la structure d’intervalle).|  
|SQL_GUID|16 (la taille de la structure GUID).|  
| &nbsp; | &nbsp; |

 [a] Si le conducteur ne peut pas déterminer la longueur de colonne ou de paramètre pour les types variables, il retourne SQL_NO_TOTAL.
