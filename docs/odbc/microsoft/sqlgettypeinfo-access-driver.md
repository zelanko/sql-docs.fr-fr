---
title: SQLGetTypeInfo (Access Driver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 788f0b8c69636ad9bf93de73632abc911a0fb0e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67898755"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations d’accès spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans la table produite par **SQLGetTypeInfo** sera le nom plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE s’affichera dans la colonne de recherche pour l’octet, compteur, Double, types de données unique, longue et courte. (La fonctionnalité LIKE est possible en convertissant la valeur en un caractère en utilisant les fonctions de conversion canonique ODBC, puis effectuer la comparaison.)
