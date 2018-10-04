---
title: Définition des champs de descripteur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14724a5cc863074344cfbb02615f0ccff228f04c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628417"
---
# <a name="setting-descriptor-fields"></a>Définition des champs de descripteur
Pour modifier les champs d’un descripteur, une application peut appeler **SQLSetDescField**. Certains champs sont en lecture seule et ne peut pas être définies. (Consultez le [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) description de fonction.)  
  
 Champs d’enregistrement descripteur sont définis avec un numéro d’enregistrement (*RecNumber*) de 1 ou version ultérieure, while champs d’en-tête de descripteur sont définis avec un numéro d’enregistrement de 0. Un numéro d’enregistrement de 0 est également utilisé pour définir les champs de signet, conformément à la convention que les signets sont contenus dans la colonne 0. Cela peut laisser l’impression que les champs de signet sont contenus dans l’en-tête de descripteur, mais cela n’est pas le cas. Champs de signet sont distincts de champs d’en-tête.  
  
 Lors de la définition des champs individuellement, votre application doit respecter l’ordre défini dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Définition de certains champs provoque le pilote définir d’autres champs. Cela garantit que le descripteur est toujours prêt à utiliser une fois que l’application a spécifié un type de données. Lorsque l’application définit le champ SQL_DESC_TYPE, le pilote vérifie que les autres champs qui spécifient le type sont valides et cohérentes.  
  
 Si un appel de fonction qui définirait un champ de descripteur échoue, le contenu du champ de descripteur est non défini après l’appel de fonction qui a échoué.
