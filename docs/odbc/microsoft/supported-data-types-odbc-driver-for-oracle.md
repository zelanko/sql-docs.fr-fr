---
title: Prise en charge des Types de données (pilote ODBC pour Oracle) | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915671"
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>Types de données pris en charge (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge tous les types de données Oracle 7.3 ; Toutefois, il ne prend pas en charge des nouveaux types de données Oracle8 répertoriées ici.  
  
|Type de données|Oracle 7.3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|N/A|Non pris en charge|  
|BLOB|N/A|Non pris en charge|  
|CHAR|Pris en charge|Pris en charge|  
|CLOB|N/A|Non pris en charge|  
|DATE|Pris en charge|Pris en charge|  
|FLOAT|Pris en charge|Pris en charge|  
|INTEGER|Pris en charge|Pris en charge|  
|LONG|Pris en charge|Pris en charge|  
|LONG RAW|Pris en charge|Pris en charge|  
|NCHAR|N/A|Non pris en charge|  
|NCLOB|N/A|Non pris en charge|  
|NUMBER|Pris en charge|Pris en charge|  
|NVARCHAR2|N/A|Non pris en charge|  
|RAW|Pris en charge|Pris en charge|  
|VARCHAR2|Pris en charge|Pris en charge|  
|MLSLABEL|Non pris en charge.|Non pris en charge.|  
  
> [!NOTE]  
>  Pour plus d’informations sur la taille autorisée de la colonne VARCHAR, consultez [taille des colonnes VARCHAR](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) dans ce guide.
