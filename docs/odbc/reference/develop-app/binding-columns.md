---
title: Liaison de colonnes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fca4cfb1455c91ca57f7b1769266e2040d6a3511
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301820"
---
# <a name="binding-columns"></a>Liaison de colonnes
Les données extraites de la source de données sont retournées à l’application dans les variables que l’application a allouées à cet effet. Avant de pouvoir effectuer cette opération, l’application doit associer, ou *lier*, ces variables aux colonnes du jeu de résultats. Conceptuellement, ce processus est identique à la liaison de variables d’application à des paramètres d’instruction. Lorsque l’application lie une variable à une colonne de jeu de résultats, elle décrit cette adresse variable, le type de données, et ainsi de suite, le pilote. Le pilote stocke ces informations dans la structure qu’il gère pour cette instruction et utilise ces informations pour retourner la valeur de la colonne lors de l’extraction de la ligne.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison des colonnes d’un ensemble de résultats](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Utilisation de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
