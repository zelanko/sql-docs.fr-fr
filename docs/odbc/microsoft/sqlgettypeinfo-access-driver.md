---
description: SQLGetTypeInfo (pilote Access)
title: SQLGetTypeInfo (pilote Access) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1ba0e135944a3ccfff454af0ff2ecc70512af2c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340075"
---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Le nom du type (TYPE_NAME) retourné dans la table produite par **SQLGetTypeInfo** sera le nom le plus couramment utilisé par la source de données.  
  
 SQL_ALL_EXCEPT_LIKE sont renvoyées dans la colonne de recherche pour les types de données Byte, Counter, double, Single, long et Short. (La capacité similaire peut être obtenue en convertissant la valeur en un caractère à l’aide des fonctions de conversion canonique ODBC, puis en effectuant la comparaison.)
