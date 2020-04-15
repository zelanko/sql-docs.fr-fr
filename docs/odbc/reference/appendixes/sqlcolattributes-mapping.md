---
title: Cartographie SQLColAttributes (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5c2c8386d6771141eaa0145a5d5964d70d6084d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305415"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes, mappage
Lorsqu’une demande appelle **SQLColAttributes** par l’intermédiaire d’un conducteur *ODBC 3.x,* l’appel à **SQLColAttributes** est cartographié à **SQLColAttribute** comme suit :  
  
> [!NOTE]
>  Le préfixe utilisé dans les valeurs *FieldIdentifier* dans ODBC *3.x* a été changé par rapport à celui utilisé dans ODBC *2.x*. Le nouveau préfixe est "SQL_DESC"; l’ancien préfixe était "SQL_COLUMN".  
  
1.  Si l’application est une application ODBC *2.x,* *fDescType* est SQL_COLUMN_TYPE, et le type retourné est un type JOURTIME concis, le Gestionnaire de pilote cartographie les valeurs de retour pour les codes date, heure et timetamp.  
  
2.  Si *fDescType* est SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE ou SQL_COLUMN_COUNT, le gestionnaire de conducteur appelle **SQLColAttribute** dans le conducteur avec *l’argument FieldIdentifier* cartographié pour SQL_DESC_NAME, SQL_DESC_NULLABLE ou SQL_DESC_COUNT, le cas échéant *.* Toutes les autres valeurs de *fDescType* sont transmises au conducteur.  
  
 Un pilote ODBC *3.x* doit prendre en charge tous les *3.x* *FieldIdentificateurs* ODBC répertoriés pour **SQLColAttribute**.  
  
 Un conducteur ODBC *3.x* doit prendre en charge SQL_COLUMN_PRECISION et SQL_DESC_PRECISION, SQL_COLUMN_SCALE et SQL_DESC_SCALE, ainsi que SQL_COLUMN_LENGTH et SQL_DESC_LENGTH. Ces valeurs sont différentes parce que la précision, l’échelle et la longueur sont définies différemment dans ODBC *3.x* qu’ils ne l’étaient dans ODBC *2.x*. Pour plus d’informations, voir [Taille de colonne, chiffres décimaux, Longueur Octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) à l’annexe D : Types de données.
