---
title: SQLGetTypeInfo (Paradox Driver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20b5776b5b0e1490ef31ff07d1876afef326db9b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63284992"
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans la table produite par **SQLGetTypeInfo** sera le nom plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE s’affichera dans la colonne de recherche pour l’octet, compteur, Double, types de données unique, longue et courte. (La fonction LIKE peut être obtenue en convertissant la valeur en un caractère en utilisant les fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)
