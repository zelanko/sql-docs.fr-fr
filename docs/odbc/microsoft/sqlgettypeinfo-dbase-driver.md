---
title: SQLGetTypeInfo (dBASE Driver) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43319f7f23741a1533321c9369077d42a2484395
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898748"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations de dBASE spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans la table produite par **SQLGetTypeInfo** sera le nom plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE s’affichera dans la colonne de recherche pour l’octet, compteur, Double, types de données unique, longue et courte. (La fonctionnalité LIKE est possible en convertissant la valeur en un caractère en utilisant les fonctions de conversion canonique ODBC, puis effectuer la comparaison.)
