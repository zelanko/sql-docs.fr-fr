---
title: Mode Batch | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c25cd688b5d74e4514e1af645f7917059ce4d445
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602397"
---
# <a name="batch-mode"></a>Mode Lot
Mode de traitement par lots est activé lorsque la **LockType** propriété est définie sur **adLockBatchOptimistic** et la mise à jour par lots est pris en charge par le fournisseur. Certains paramètres de verrouillage ne sont pas disponibles en fonction de l’emplacement du curseur. Par exemple, un type de verrouillage pessimiste n’est pas disponible lorsque le **CursorLocation** a la valeur **adUseClient**. À l’inverse, un fournisseur ne peut pas prend en charge un verrouillage optimiste lot lors de l’emplacement du curseur est sur le serveur. Vous devez utiliser le traitement par lots de la mise à jour avec un jeu de clés ou un curseur statique uniquement.  
  
 Le **UpdateBatch** méthode est utilisée pour envoyer **Recordset** modifications contenues dans la mémoire tampon de copie vers le serveur pour mettre à jour la source de données. Dans la section suivante, nous allons ouvrir un **Recordset** en mode batch, apporter des modifications à la mémoire tampon de copie, puis l’envoi des modifications à la source de données à l’aide d’un appel à **UpdateBatch**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Envoi des mises à jour : méthode UpdateBatch](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Filtrage des enregistrements mis à jour](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Traitement des mises à jour ayant échoué](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Détection et résolution des conflits](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Déconnexion et reconnexion du recordset](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Mise à jour des résultats d’une jointure : table unique](../../../ado/guide/data/updating-joined-results-unique-table.md)
