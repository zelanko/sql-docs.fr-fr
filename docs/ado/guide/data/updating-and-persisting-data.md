---
title: Mise à jour et persistance des données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updating data [ADO]
- data updates [ADO]
- ADO, updating data
ms.assetid: 8dc27274-4f96-43d1-913c-4ff7d01b9a27
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 26fabdc205018b8e94575cfb5bd5e945a8fb28ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923722"
---
# <a name="updating-and-persisting-data"></a>Mise à jour et enregistrement des données
Les chapitres précédents ont expliqué comment utiliser ADO pour accéder aux données d’une source de données, comment se déplacer dans les données, et même comment modifier les données. Bien sûr, si l’objectif de votre application est de permettre aux utilisateurs d’apporter des modifications aux données, vous devrez comprendre comment enregistrer ces modifications. Vous pouvez conserver les modifications apportées au **jeu d’enregistrements** dans un fichier à l’aide de la méthode **Save** , ou vous pouvez renvoyer les modifications à la source de données pour le stockage à l’aide des méthodes **Update** ou **UpdateBatch** .  
  
 Dans les chapitres précédents, vous avez modifié les données de plusieurs lignes de l’ensemble d' **enregistrements**. ADO prend en charge deux notions de base relatives à l’ajout, la suppression et la modification des lignes de données.  
  
 La première notion est que les modifications ne sont pas immédiatement envoyées au **Recordset**; au lieu de cela, ils sont passés à un *tampon de copie*interne. Si vous décidez que vous ne souhaitez pas les modifier, les modifications dans le tampon de copie sont ignorées. Si vous décidez de conserver les modifications, les modifications apportées à la mémoire tampon de copie sont appliquées au **jeu d’enregistrements**.  
  
 La deuxième notion est que les modifications sont propagées à la source de données dès que vous déclarez le travail sur une ligne terminée (c’est-à-dire, le mode *immédiat* ), ou toutes les modifications apportées à un ensemble de lignes sont collectées jusqu’à ce que vous déclariez le travail pour l’ensemble terminé (autrement dit, le mode *batch* ). La propriété **LockType** détermine le moment où les modifications sont apportées à la source de données sous-jacente. **adLockOptimistic** ou **adLockPessimistic** spécifie le mode immédiat, tandis que **adLockBatchOptimistic** spécifie le mode batch. La propriété **CursorLocation** peut affecter les paramètres de **LockType** disponibles. Par exemple, le paramètre **adLockPessimistic** n’est pas pris en charge si la propriété **CursorLocation** a la valeur **adUseClient**.  
  
 En mode exécution, chaque appel de la méthode **Update** propage les modifications à la source de données. En mode batch, chaque appel de **mise à jour** ou de déplacement de la position de ligne actuelle enregistre les modifications dans la mémoire tampon de copie, mais seule la méthode **UpdateBatch** propage les modifications à la source de données.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mise à jour des données](../../../ado/guide/data/updating-data.md)  
  
-   [Persistance des données](../../../ado/guide/data/persisting-data.md)
