---
title: Colonnes de liaison Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301820"
---
# <a name="binding-columns"></a>Liaison de colonnes
Les données récupérées à partir de la source de données sont retournées à l’application dans les variables que l’application a allouées à cette fin. Avant que cela puisse être fait, l’application doit associer, ou *lier,* ces variables aux colonnes de l’ensemble de résultat; conceptuellement, ce processus est le même que les variables d’application contraignantes aux paramètres d’énoncé. Lorsque l’application lie une variable à une colonne d’ensemble de résultats, elle décrit cette variable - adresse, type de données, etc. - au pilote. Le conducteur stocke ces informations dans la structure qu’il maintient pour cette déclaration et utilise les informations pour retourner la valeur de la colonne lorsque la rangée est récupérée.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Liaison des colonnes d’un ensemble de résultats](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [Utilisation de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)
