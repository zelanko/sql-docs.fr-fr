---
title: Mappage de SQLColAttributes | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d21d1a9a9565ad2c0accbebb716d0b24f18f854d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcolattributes-mapping"></a>Mappage de SQLColAttributes
Lorsqu’une application appelle **SQLColAttributes** via un ODBC 3*.x* pilote, l’appel à **SQLColAttributes** est mappé à **SQLColAttribute** comme suit :  
  
> [!NOTE]  
>  Le préfixe utilisé dans *FieldIdentifier* valeurs dans ODBC 3*.x* a été modifié depuis qu’utilisés dans ODBC 2.* x*. Le nouveau préfixe est « SQL_DESC » ; le préfixe ancien a été « SQL_COLUMN ».  
  
1.  Si l’application est une API ODBC 2. *x* application, *fDescType* est SQL_COLUMN_TYPE, et le type retourné est un type DATETIME concis, les mappages de gestionnaire de pilotes le retour des valeurs pour les codes de date, time et timestamp.  
  
2.  Si *fDescType* est SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE ou SQL_COLUMN_COUNT, les appels du Gestionnaire de pilotes **SQLColAttribute** dans le pilote avec la *FieldIdentifier* argument mappé à SQL_DESC_NAME, SQL_DESC_NULLABLE ou SQL_DESC_COUNT, selon le cas*.* Toutes les autres valeurs de *fDescType* sont transmises au pilote.  
  
 Un ODBC 3*.x* pilote doit prendre en charge tous les ODBC 3*.x* *FieldIdentifiers* répertoriés pour **SQLColAttribute**.  
  
 Un ODBC 3*.x* pilote doit prendre en charge SQL_COLUMN_PRECISION et SQL_DESC_PRECISION, SQL_COLUMN_SCALE et SQL_DESC_SCALE et SQL_COLUMN_LENGTH et SQL_DESC_LENGTH. Ces valeurs sont différentes, car la précision, échelle et longueur sont définis différemment dans ODBC 3*.x* qu’ils étaient dans ODBC 2.* x*. Pour plus d’informations, consultez [taille de colonne, des chiffres décimaux, transférer la longueur en octets et la taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) annexe d : Types de données.
