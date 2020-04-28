---
title: SQLGetTypeInfo (pilote dBASE) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81295129"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans la table produite par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sont renvoyées dans la colonne de recherche pour les types de données Byte, Counter, double, Single, long et Short. (La capacité similaire peut être obtenue en convertissant la valeur en un caractère à l’aide des fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)
