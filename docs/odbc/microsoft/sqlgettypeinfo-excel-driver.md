---
title: SQLGetTypeInfo (Excel Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Excel Driver
- Excel driver [ODBC], SQLGetTypeInfo
ms.assetid: 708845be-e6a1-4677-8113-c52819a43fa4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64befe30be9ed7988e0c9348e9335eb632dd975c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295069"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (pilote Excel)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Excel Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans le tableau produit par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sera retournée dans la colonne SEARCHABLE pour les types de données Byte, Counter, Double, Single, Long et Short. (La capacité LIKE peut être atteinte en convertissant la valeur en un personnage en utilisant les fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)  
  
 Lorsque le pilote Microsoft Excel est utilisé, les noms de type ODBC sont retournés dans la colonne TYPE_NAME qui est retournée par **SQLGetTypeInfo**.
