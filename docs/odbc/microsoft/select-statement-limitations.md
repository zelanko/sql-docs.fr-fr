---
title: Limitations de l’instruction SELECT | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26bf17596dbd3279498df2edcee7636db95ae139
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127852"
---
# <a name="select-statement-limitations"></a>SELECT, instruction - limitations
Une colonne de la fonction d’agrégation ne peut pas être combinée avec une colonne non agrégée dans une instruction SELECT.  
  
 La liste de sélection d’une instruction SELECT qui contient une clause GROUP BY peut contenir uniquement des expressions de la clause GROUP BY ou définir des fonctions.  
  
 L’utilisation d’un astérisque (pour sélectionner toutes les colonnes) dans une instruction SELECT contenant une clause GROUP BY n’est pas pris en charge. Les noms des colonnes à sélectionner doivent être spécifiés.  
  
 L’utilisation d’une barre verticale dans une instruction SELECT n’est pas pris en charge. Utiliser un paramètre dans l’instruction SELECT si vous avez besoin faire référence à une valeur de données qui contient une barre verticale.  
  
 Lorsque vous utilisez un alias de colonne dans une instruction SELECT, le mot « sous » doit précéder l’alias. Par exemple, « SELECT col1 comme un à partir de b. » Sans le « comme », l’instruction retourne une erreur.  
  
 Si un nom de colonne incorrect est entré dans une instruction SELECT, une erreur SQLSTATE 07001, « Nombre de paramètres erronés, » est retournée au lieu d’une erreur SQLSTATE S0022, « colonne Not Found. »  
  
 Lorsque le pilote Microsoft Excel est utilisé, si une chaîne vide est insérée dans une colonne, la chaîne vide est convertie en une valeur NULL ; une instruction SELECT recherchée qui est exécutée avec une chaîne vide dans la clause WHERE ne réussira pas sur cette colonne.
