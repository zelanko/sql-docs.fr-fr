---
description: SQLGetTypeInfo (pilote Excel)
title: SQLGetTypeInfo (pilote Excel) | Microsoft Docs
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
ms.openlocfilehash: ca7e70d9f26a87ededb21bc6c48f3d3cd31d8af3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339955"
---
# <a name="sqlgettypeinfo-excel-driver"></a>SQLGetTypeInfo (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans la table produite par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sont renvoyées dans la colonne de recherche pour les types de données Byte, Counter, double, Single, long et Short. (La capacité similaire peut être obtenue en convertissant la valeur en un caractère à l’aide des fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)  
  
 Lorsque le pilote Microsoft Excel est utilisé, les noms de type ODBC sont retournés dans le TYPE_NAME colonne renvoyée par **SQLGetTypeInfo**.
