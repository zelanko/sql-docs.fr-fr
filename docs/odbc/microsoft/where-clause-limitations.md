---
description: WHERE, clause - limitations
title: Limitations des clauses WHERE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, WHERE clause limitations
- WHERE clause limitations [ODBC]
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8b6b9e72176f447c71daccfbd0393f414558d49d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466281"
---
# <a name="where-clause-limitations"></a>WHERE, clause - limitations
Le nombre maximal de clauses dans une clause WHERE est 40.  
  
 Les colonnes LONGVARBINARY et LONGVARCHAR peuvent être comparées à des littéraux d’une longueur maximale de 255 caractères, mais elles ne peuvent pas être comparées à l’aide de paramètres.
