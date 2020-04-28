---
title: Mappage des types de données (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 432c21b70efcdd63ef36bfe3d26f8488ddb11d1d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302670"
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>Mappage des types de données (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le serveur Oracle prend en charge un ensemble de types de données. Le pilote ODBC pour Oracle mappe ces types de données aux types de données SQL ODBC appropriés. Le tableau suivant répertorie les types de données du serveur Oracle 7,3 et leurs types de données SQL ODBC correspondants.  
  
 Le pilote ODBC pour Oracle prend en charge Oracle 7,3 et certains types de données Oracle8. Pour plus d’informations sur les types de données Oracle8 pris en charge, consultez [types de données pris en charge](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md).  
  
|Type de données du serveur Oracle|Type de données SQL ODBC|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  Pour plus d’informations sur la taille autorisée de la colonne VARCHAR, consultez [varchar Column Size](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md) dans ce guide.
