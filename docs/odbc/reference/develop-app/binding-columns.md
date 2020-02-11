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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a634a553672b83931091056dd489f7559c4269b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106213"
---
# <a name="binding-columns"></a>Liaison de colonnes
Les données extraites de la source de données sont retournées à l’application dans les variables que l’application a allouées à cet effet. Avant de pouvoir effectuer cette opération, l’application doit associer, ou *lier*, ces variables aux colonnes du jeu de résultats. Conceptuellement, ce processus est identique à la liaison de variables d’application à des paramètres d’instruction. Lorsque l’application lie une variable à une colonne de jeu de résultats, elle décrit cette adresse variable, le type de données, et ainsi de suite, le pilote. Le pilote stocke ces informations dans la structure qu’il gère pour cette instruction et utilise ces informations pour retourner la valeur de la colonne lors de l’extraction de la ligne.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison des colonnes d’un ensemble de résultats](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Utilisation de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
