---
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
ms.openlocfilehash: 1699397db81d6fe702f60f6953fe7a0ae3726fe3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307560"
---
# <a name="where-clause-limitations"></a>WHERE, clause - limitations
Le nombre maximal de clauses dans une clause WHERE est 40.  
  
 Les colonnes LONGVARBINARY et LONGVARCHAR peuvent être comparées à des littéraux d’une longueur maximale de 255 caractères, mais elles ne peuvent pas être comparées à l’aide de paramètres.
