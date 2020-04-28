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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 313254a3a117984d666d7c7be7e506386ae34e3b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301114"
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>Types de données pris en charge (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge tous les types de données Oracle 7,3. Toutefois, il ne prend pas en charge les nouveaux types de données Oracle8 répertoriés ici.  
  
|Type de données|Oracle 7,3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|n/a|Non prise en charge|  
|BLOB|n/a|Non prise en charge|  
|CHAR|Pris en charge|Pris en charge|  
|CLOB|n/a|Non prise en charge|  
|DATE|Pris en charge|Pris en charge|  
|FLOAT|Pris en charge|Pris en charge|  
|INTEGER|Pris en charge|Pris en charge|  
|LONG|Pris en charge|Pris en charge|  
|LONG RAW|Pris en charge|Pris en charge|  
|NCHAR|n/a|Non prise en charge|  
|NCLOB|n/a|Non prise en charge|  
|NUMBER|Pris en charge|Pris en charge|  
|NVARCHAR2|n/a|Non prise en charge|  
|RAW|Pris en charge|Pris en charge|  
|VARCHAR2|Pris en charge|Pris en charge|  
|MLSLABEL|Non pris en charge.|Non pris en charge.|  
  
> [!NOTE]  
>  Pour plus d’informations sur la taille autorisée de la colonne VARCHAR, consultez [varchar Column Size](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) dans ce guide.
