---
title: SQLGetTypeInfo (Text File Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b70b58e4760959db102450b5f8b7beed042df95
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294999"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (pilote de fichier texte)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques au fichier texte. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans le tableau produit par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sera retournée dans la colonne SEARCHABLE pour les types de données Byte, Counter, Double, Single, Long et Short. (La capacité LIKE peut être atteinte en convertissant la valeur en un personnage en utilisant les fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)  
  
 Lorsque le pilote de texte est utilisé, **SQLGetTypeInfo** renvoie une valeur CASE_SENSITIVE de FALSE pour les types de données textuelles (CHAR et LONGCHAR), lorsque les types de données sont réellement sensibles aux cas.
