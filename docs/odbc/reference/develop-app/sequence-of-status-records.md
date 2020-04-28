---
title: Séquence d’enregistrements d’État | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb26731a85d1d6313658fe9c24a32167b351d2d9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304170"
---
# <a name="sequence-of-status-records"></a>Séquence d’enregistrements d’état
Si au moins deux enregistrements d’État sont renvoyés, le gestionnaire de pilotes et le pilote sont classés en fonction des règles suivantes. L’enregistrement avec le rang le plus élevé est le premier enregistrement. La source d’un enregistrement (gestionnaire de pilotes, pilote, passerelle, etc.) n’est pas prise en compte lors du classement des enregistrements.  
  
-   **Erreurs** Les enregistrements d’État qui décrivent les erreurs ont le rang le plus élevé. Parmi les enregistrements d’erreur, les enregistrements qui indiquent un échec de transaction ou un échec de transaction possible dérangent tous les autres enregistrements. Si deux ou plusieurs enregistrements décrivent la même condition d’erreur, les SQLSTATEs définies par la spécification Open CLI de groupe (classes 03 à HZ) sont prioritaires par rapport aux SQLSTATEs définies par ODBC et définies par le pilote.  
  
-   **Aucune valeur de données définie par l’implémentation** Les enregistrements d’État qui décrivent les valeurs de données non définies par le pilote (classe 02) ont le deuxième rang le plus élevé.  
  
-   **Avertissements** Les enregistrements d’État qui décrivent les avertissements (classe 01) ont le rang le plus bas. Si deux ou plusieurs enregistrements décrivent la même condition d’avertissement, les SQLSTATE d’avertissement définis par la spécification CLI de groupe ouverte sont prioritaires par rapport aux SQLSTATEs définies par ODBC et par le pilote.  
  
 Si deux enregistrements ou plus ont le rang le plus élevé, il n’est pas défini quel enregistrement est le premier enregistrement. L’ordre de tous les autres enregistrements n’est pas défini. En particulier, étant donné que les avertissements peuvent apparaître avant les erreurs, les applications doivent vérifier tous les enregistrements d’État lorsqu’une fonction retourne une valeur autre que SQL_SUCCESS.
