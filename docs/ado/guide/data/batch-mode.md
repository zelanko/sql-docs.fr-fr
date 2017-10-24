---
title: Mode de traitement par lots | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92e249a7c2d5b0c01e291f4829d5c4f8c580fb2c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="batch-mode"></a>Mode Lot
Mode de traitement par lots est activé lorsque la **LockType** est définie sur **adLockBatchOptimistic** et mise à jour par lot est pris en charge par le fournisseur. Certains paramètres de verrouillage ne sont pas disponibles en fonction de l’emplacement du curseur. Par exemple, un type de verrouillage pessimiste n’est pas disponible lorsque le **CursorLocation** a la valeur **adUseClient**. À l’inverse, un fournisseur ne prendre en charge un verrouillage optimiste du traitement par lots lorsque l’emplacement du curseur se trouve sur le serveur. Vous devez utiliser les commandes de mise à jour avec un jeu de clés ou un curseur statique uniquement.  
  
 Le **UpdateBatch** méthode est utilisée pour envoyer **Recordset** modifications contenues dans le tampon de copie au serveur pour mettre à jour la source de données. Dans la section suivante, nous allons ouvrir un **Recordset** en mode batch, apporter des modifications à la mémoire tampon de copie, puis l’envoi des modifications à la source de données à l’aide d’un appel à **UpdateBatch**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Envoyer les mises à jour : méthode UpdateBatch](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Filtrage des enregistrements mis à jour](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Traitement des mises à jour ayant échouées](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Détection et résolution des conflits](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Déconnexion et reconnexion de l’ensemble d’enregistrements](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Mise à jour joint les résultats : Une Table Unique](../../../ado/guide/data/updating-joined-results-unique-table.md)

