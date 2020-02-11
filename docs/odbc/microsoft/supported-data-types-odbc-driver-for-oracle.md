---
title: Types de données pris en charge (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 145170afee5ab791602695c662ce1e80e86cae7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915671"
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>Types de données pris en charge (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge tous les types de données Oracle 7,3. Toutefois, il ne prend pas en charge les nouveaux types de données Oracle8 répertoriés ici.  
  
|Type de données|Oracle 7,3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|n/a|Non pris en charge|  
|BLOB|n/a|Non pris en charge|  
|CHAR|Prise en charge|Prise en charge|  
|CLOB|n/a|Non pris en charge|  
|DATE|Prise en charge|Prise en charge|  
|FLOAT|Prise en charge|Prise en charge|  
|INTEGER|Prise en charge|Prise en charge|  
|LONG|Prise en charge|Prise en charge|  
|LONG RAW|Prise en charge|Prise en charge|  
|NCHAR|n/a|Non pris en charge|  
|NCLOB|n/a|Non pris en charge|  
|NUMBER|Prise en charge|Prise en charge|  
|NVARCHAR2|n/a|Non pris en charge|  
|RAW|Prise en charge|Prise en charge|  
|VARCHAR2|Prise en charge|Prise en charge|  
|MLSLABEL|Non pris en charge.|Non pris en charge.|  
  
> [!NOTE]  
>  Pour plus d’informations sur la taille autorisée de la colonne VARCHAR, consultez [varchar Column Size](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) dans ce guide.
