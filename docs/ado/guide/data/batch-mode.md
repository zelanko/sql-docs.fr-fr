---
description: Mode Lot
title: Mode batch | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 353e5ae0fe15fb21f04f6efcc97195a5e237b58e
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806393"
---
# <a name="batch-mode"></a>Mode Lot
Le mode batch est activé lorsque la propriété **LockType** est définie sur **adLockBatchOptimistic** et que la mise à jour par lot est prise en charge par le fournisseur. Certains paramètres de type de verrou ne sont pas disponibles en fonction de l’emplacement du curseur. Par exemple, un type de verrou pessimiste n’est pas disponible lorsque **CursorLocation** a la valeur **adUseClient**. À l’inverse, un fournisseur ne peut pas prendre en charge un verrou optimiste par lot lorsque l’emplacement du curseur se trouve sur le serveur. Vous devez utiliser la mise à jour par lot avec un curseur de jeu de clés ou statique uniquement.  
  
 La méthode **UpdateBatch** est utilisée pour envoyer les modifications de l’ensemble **d’enregistrements** contenues dans la mémoire tampon de copie sur le serveur pour mettre à jour la source de données. Dans la section suivante, nous allons ouvrir un **Recordset** en mode batch, apporter des modifications à la mémoire tampon de copie, puis envoyer nos modifications à la source de données à l’aide d’un appel à **UpdateBatch**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Envoi des mises à jour : UpdateBatch, méthode](./sending-the-updates-updatebatch-method.md)  
  
-   [Filtrage des enregistrements mis à jour](./filtering-for-updated-records.md)  
  
-   [Traitement des mises à jour ayant échoué](./dealing-with-failed-updates.md)  
  
-   [Détection et résolution des conflits](./detecting-and-resolving-conflicts.md)  
  
-   [Déconnexion et reconnexion du recordset](./disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Mise à jour des résultats d’une jointure : table unique](./updating-joined-results-unique-table.md)