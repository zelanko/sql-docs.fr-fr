---
title: Séquence d’enregistrements d’état | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 67eac22a630305f32f141ea18861e5638445f19b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094350"
---
# <a name="sequence-of-status-records"></a>Séquence d’enregistrements d’état
Si deux ou plusieurs enregistrements d’état sont retournés, le Gestionnaire de pilotes et le pilote classent selon les règles suivantes. L’enregistrement avec le rang le plus élevé est le premier enregistrement. La source d’un enregistrement (Gestionnaire de pilotes, pilotes, passerelle et ainsi de suite) constitue toutefois pas lorsque les enregistrements de classement.  
  
-   **Erreurs** enregistrements d’état qui décrivent les erreurs ont le rang le plus élevé. Parmi les enregistrements d’erreur, les enregistrements qui indiquent un échec de la transaction ou l’échec de la transaction possible outrank tous les autres enregistrements. Si deux ou plusieurs enregistrements décrivent la condition d’erreur, SQLSTATE défini par la spécification Open groupe CLI (classes 03 via HZ) outrank SQLSTATE définies par ODBC et définis par le pilote.  
  
-   **Les valeurs de données non défini par l’implémentation** enregistrements d’état qui décrivent les valeurs des données de non définis par le pilote (classe 02) ont la deuxième rang le plus élevé.  
  
-   **Avertissements** enregistrements d’état qui décrivent les avertissements (classe 01) ont le rang le plus bas. Si deux ou plusieurs enregistrements décrivent la même condition d’avertissement, avertissement SQLSTATE défini par la spécification Open groupe CLI outrank SQLSTATE définies par ODBC et définis par le pilote.  
  
 S’il existe deux ou plusieurs enregistrements avec le rang le plus élevé, il n’est pas définie qui n’est le premier enregistrement. L’ordre de tous les autres enregistrements n’est pas défini. En particulier, étant donné que les avertissements peuvent apparaître avant les erreurs, les applications doivent vérifier tous les enregistrements d’état lorsqu’une fonction retourne une valeur autre que SQL_SUCCESS.
