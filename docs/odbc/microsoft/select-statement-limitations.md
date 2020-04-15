---
title: Limitations de déclaration SELECT (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d91e93076a67287cbbd2b64b2ad0d6414a0aea6d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300919"
---
# <a name="select-statement-limitations"></a>SELECT, instruction - limitations
Une colonne de fonction globale ne peut pas être mélangée à une colonne non agrégée dans une instruction SELECT.  
  
 La liste sélectionnée d’une déclaration SELECT qui a une clause GROUPE BY ne peut avoir que des expressions de la clause GROUPE BY ou des fonctions définies.  
  
 L’utilisation d’un astérisque (pour sélectionner toutes les colonnes) dans une déclaration SELECT contenant une clause GROUPE BY n’est pas prise en charge. Les noms des colonnes à sélectionner doivent être spécifiés.  
  
 L’utilisation d’une barre verticale dans une déclaration SELECT n’est pas prise en charge. Utilisez un paramètre dans l’instruction SELECT si vous devez vous référer à une valeur de données qui contient une barre verticale.  
  
 Lors de l’utilisation d’un alias colonne dans une déclaration SELECT, le mot "comme" doit précéder l’alias. Par exemple, "SELECT col1 comme un de b." Sans le "as", la déclaration va retourner une erreur.  
  
 Si un nom de colonne incorrect est entré dans une déclaration SELECT, une erreur SQLSTATE 07001, « Mauvais nombre de paramètres », est retournée au lieu d’une erreur SQLSTATE S0022, « Colonne non trouvée ».  
  
 Lorsque le pilote Microsoft Excel est utilisé, si une chaîne vide est insérée dans une colonne, la chaîne vide est convertie en NULL ; une instruction SELECT recherchée qui est exécutée avec une chaîne vide dans la clause WHERE ne réussira pas sur cette colonne.
