---
title: SQLGetTypeInfo (pilote de fichier texte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2659b3251cf77882f3762ce5699c36441e6c8ebc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898650"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans la table produite par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sont renvoyées dans la colonne de recherche pour les types de données Byte, Counter, double, Single, long et Short. (La capacité similaire peut être obtenue en convertissant la valeur en un caractère à l’aide des fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)  
  
 Lorsque le pilote de texte est utilisé, **SQLGetTypeInfo** retourne un CASE_SENSITIVE valeur false pour les types de données texte (char et LongChar), lorsque les types de données respectent la casse.
