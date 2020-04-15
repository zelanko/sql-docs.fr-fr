---
title: Réglage des champs descripteur (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 04f9520e2ef462df481bb104e389aeb57b5dd457
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304150"
---
# <a name="setting-descriptor-fields"></a>Définition des champs de descripteur
Pour modifier les champs d’un descripteur, une application peut appeler **SQLSetDescField**. Certains champs sont lus uniquement et ne peuvent pas être définis. (Voir la description de la fonction [SQLSetDescField.)](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 Les champs d’enregistrement descripteur sont fixés avec un nombre record (*RecNumber*) de 1 ou plus, tandis que les champs d’en-tête descripteur sont fixés avec un nombre record de 0. Un nombre record de 0 est également utilisé pour définir des champs de signets, conformément à la convention selon laquelle les signets sont contenus dans la colonne 0. Cela pourrait laisser l’impression que les champs de signets sont contenus dans l’en-tête descripteur, mais ce n’est pas le cas. Les champs de signets sont distincts des champs d’en-tête.  
  
 Lors de la mise en place des champs individuellement, l’application doit suivre la séquence définie dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). La mise en place de certains champs amène le conducteur à définir d’autres champs. Cela garantit que le descripteur est toujours prêt à l’emploi une fois que l’application a spécifié un type de données. Lorsque l’application définit le champ SQL_DESC_TYPE, le conducteur vérifie que les autres champs qui spécifient le type sont valides et cohérents.  
  
 Si un appel de fonction qui définirait un champ descripteur échoue, le contenu du champ descripteur n’est pas défini après l’appel de fonction raté.
