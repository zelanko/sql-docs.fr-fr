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
ms.openlocfilehash: 188a95f985ac1d578bca8c7e10ac4c4054c935c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925954"
---
# <a name="batch-mode"></a>Mode Lot
Mode de traitement par lots est activé lorsque la **LockType** propriété est définie sur **adLockBatchOptimistic** et la mise à jour par lots est pris en charge par le fournisseur. Certains paramètres de verrouillage ne sont pas disponibles en fonction de l’emplacement du curseur. Par exemple, un type de verrouillage pessimiste n’est pas disponible lorsque le **CursorLocation** a la valeur **adUseClient**. À l’inverse, un fournisseur ne peut pas prend en charge un verrouillage optimiste lot lors de l’emplacement du curseur est sur le serveur. Vous devez utiliser le traitement par lots de la mise à jour avec un jeu de clés ou un curseur statique uniquement.  
  
 Le **UpdateBatch** méthode est utilisée pour envoyer **Recordset** modifications contenues dans la mémoire tampon de copie vers le serveur pour mettre à jour la source de données. Dans la section suivante, nous allons ouvrir un **Recordset** en mode batch, apporter des modifications à la mémoire tampon de copie, puis l’envoi des modifications à la source de données à l’aide d’un appel à **UpdateBatch**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Envoyer les mises à jour : UpdateBatch, méthode](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Filtrage des enregistrements mis à jour](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Traitement des mises à jour ayant échoué](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Détection et résolution des conflits](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Déconnexion et reconnexion du recordset](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Résultats d’une jointure la mise à jour : Table unique](../../../ado/guide/data/updating-joined-results-unique-table.md)
