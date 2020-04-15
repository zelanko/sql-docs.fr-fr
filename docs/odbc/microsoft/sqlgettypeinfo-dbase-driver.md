---
title: SQLGetTypeInfo (pilote dBASE) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 711652e22318d089b02fe8e79cb592f0a42dfff9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295129"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (pilote dBASE)
> [!NOTE]  
>  Ce sujet fournit dBASE Des informations spécifiques au conducteur. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans le tableau produit par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sera retournée dans la colonne SEARCHABLE pour les types de données Byte, Counter, Double, Single, Long et Short. (La capacité LIKE peut être atteinte en convertissant la valeur en un personnage en utilisant les fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)
