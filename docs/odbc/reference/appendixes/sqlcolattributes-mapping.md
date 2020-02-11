---
title: Mappage SQLColAttributes | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08abd0128a6fa2a478af0e9dc9c292ff973ace79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064488"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes, mappage
Quand une application appelle **SQLColAttributes** via un pilote ODBC *3. x* , l’appel à **SQLColAttributes** est mappé à **SQLColAttribute** comme suit :  
  
> [!NOTE]
>  Le préfixe utilisé dans les valeurs *FieldIdentifier* dans ODBC *3. x* a été modifié par rapport à celui utilisé dans ODBC *2. x*. Le nouveau préfixe est « SQL_DESC ». l’ancien préfixe était « SQL_COLUMN ».  
  
1.  Si l’application est une application ODBC *2. x* , *fDescType* est SQL_COLUMN_TYPE et que le type retourné est un type DateTime concis, le gestionnaire de pilotes mappe les valeurs de retour pour les codes de date, d’heure et d’horodatage.  
  
2.  Si *fDescType* est SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE ou SQL_COLUMN_COUNT, le gestionnaire de pilotes appelle **SQLColAttribute** dans le pilote avec l’argument *FieldIdentifier* mappé à SQL_DESC_NAME, SQL_DESC_NULLABLE ou SQL_DESC_COUNT, le cas échéant *.* Toutes les autres valeurs de *fDescType* sont transmises au pilote.  
  
 Un pilote ODBC *3. x* doit prendre en charge toutes les *FieldIdentifiers* ODBC *3. x* listées pour **SQLColAttribute**.  
  
 Un pilote ODBC *3. x* doit prendre en charge SQL_COLUMN_PRECISION et SQL_DESC_PRECISION, SQL_COLUMN_SCALE et SQL_DESC_SCALE, ainsi que SQL_COLUMN_LENGTH et SQL_DESC_LENGTH. Ces valeurs sont différentes, car la précision, l’échelle et la longueur sont définies différemment dans ODBC *3. x* que dans ODBC *2. x*. Pour plus d’informations, consultez [taille de colonne, chiffres décimaux, longueur d’octet de transfert et taille d’affichage](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) dans l’annexe D : types de données.
