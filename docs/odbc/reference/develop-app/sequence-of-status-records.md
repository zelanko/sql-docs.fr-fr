---
title: Séquence des enregistrements d’état (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304170"
---
# <a name="sequence-of-status-records"></a>Séquence d’enregistrements d’état
Si deux dossiers d’état ou plus sont retournés, le gestionnaire de conducteur et le conducteur les classent selon les règles suivantes. Le record avec le rang le plus élevé est le premier record. La source d’un dossier (Driver Manager, driver, gateway, etc.) n’est pas prise en compte lors du classement des enregistrements.  
  
-   **Erreurs** Les enregistrements d’état qui décrivent les erreurs ont le rang le plus élevé. Parmi les enregistrements d’erreur, les enregistrements indiquant une défaillance de transaction ou une éventuelle défaillance de transaction ont surclassé tous les autres enregistrements. Si deux dossiers ou plus décrivent la même condition d’erreur, les SQLSTATEs définis par les spécifications CLI du Groupe Ouvert (classes 03 par HZ) surclassent les SQLSTATes définis par ODBC et définis par le conducteur.  
  
-   **Définition de la mise en œuvre Aucune valeur de données** Les enregistrements d’état qui décrivent les valeurs sans données définies par le conducteur (classe 02) ont le deuxième rang le plus élevé.  
  
-   **Avertissements** Les dossiers d’état qui décrivent les avertissements (classe 01) ont le rang le plus bas. Si deux dossiers ou plus décrivent la même condition d’avertissement, les SQLSTATEs d’avertissement définis par les spécifications CLI du Groupe Ouvert surclassent les SQLSTATes définies par ODBC et définies par le conducteur.  
  
 S’il y a deux disques ou plus ayant le rang le plus élevé, il n’est pas défini quel record est le premier enregistrement. L’ordre de tous les autres enregistrements n’est pas défini. En particulier, parce que les avertissements peuvent apparaître avant les erreurs, les applications doivent vérifier tous les enregistrements d’état lorsqu’une fonction renvoie une valeur autre que SQL_SUCCESS.
