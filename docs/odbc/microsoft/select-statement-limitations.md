---
title: Limitations de l’instruction SELECT | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e27e435fea1aeb864eb20ac478a72860394b8f6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="select-statement-limitations"></a>Limitations de l’instruction SELECT
Une colonne de la fonction d’agrégation ne peut pas être combinée avec une colonne non agrégée dans une instruction SELECT.  
  
 La liste de sélection d’une instruction SELECT qui contient une clause GROUP BY peut contenir uniquement des expressions de la clause GROUP BY ou les fonctions de jeu.  
  
 L’utilisation d’un astérisque (pour sélectionner toutes les colonnes) dans une instruction SELECT contenant une clause GROUP BY n’est pas pris en charge. Les noms des colonnes à être sélectionné doivent être spécifiés.  
  
 L’utilisation d’une barre verticale dans une instruction SELECT n’est pas pris en charge. Utiliser un paramètre dans l’instruction SELECT si vous avez besoin faire référence à une valeur de données qui contient une barre verticale.  
  
 Lorsque vous utilisez un alias de colonne dans une instruction SELECT, le mot « as » doit précéder l’alias. Par exemple, « SELECT col1 comme un b. » Sans le « en », l’instruction retourne une erreur.  
  
 Si un nom de colonne incorrect est entré dans une instruction SELECT, une erreur SQLSTATE 07001, « Nombre de paramètres erronés, » est retournée au lieu d’une erreur SQLSTATE S0022, « colonne introuvable. »  
  
 Lorsque le pilote Microsoft Excel est utilisé, si une chaîne vide est insérée dans une colonne, une chaîne vide est convertie en une valeur NULL ; une instruction SELECT recherche qui est exécutée avec une chaîne vide dans la clause WHERE ne réussira pas sur cette colonne.
