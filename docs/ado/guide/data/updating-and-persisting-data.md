---
title: La mise à jour et persistance des données | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: d53891b4e82b3ae391d095e8cbca2189fb201d29
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758827"
---
# <a name="updating-and-persisting-data"></a>Mise à jour et enregistrement des données
Les chapitres précédents ont présenté comment utiliser ADO pour accéder aux données d’une source de données, pour vous déplacer dans les données et même comment modifier les données. Bien sûr, si l’objectif de votre application est de permettre aux utilisateurs d’apporter des modifications aux données, vous devez comprendre comment enregistrer ces modifications. Vous pouvez soit conserver la **Recordset** passe à un fichier en utilisant le **enregistrer** (méthode), ou vous pouvez envoyer les modifications dans la source de données pour le stockage à l’aide la **mise à jour** ou  **UpdateBatch** méthodes.  
  
 Dans les chapitres précédents, vous avez modifié les données dans plusieurs lignes de la **Recordset**. ADO prend en charge les deux notions de base relatives à l’ajout, la suppression et la modification des lignes de données.  
  
 La notion de premier est que les modifications ne sont pas immédiatement mises à la **Recordset**; au lieu de cela, elles sont apportées à une liste interne *tampon de copie*. Si vous décidez de ne pas les modifications, les modifications dans la mémoire tampon de copie sont ignorées. Si vous décidez de conserver les modifications, les modifications dans la mémoire tampon de copie sont appliquées à la **Recordset**.  
  
 La notion de deuxième est que les modifications soit sont propagées à la source de données dès que vous déclarez que le travail sur une ligne complète (autrement dit, *immédiate* mode), ou toutes les modifications apportées à un ensemble de lignes sont collectées jusqu'à ce que vous déclarez le travail pour le jeu complète (autrement dit, *batch* mode). Le **LockType** propriété détermine quand les modifications sont apportées à la source de données sous-jacente. **adLockOptimistic** ou **adLockPessimistic** Spécifie le mode d’exécution, tandis que **adLockBatchOptimistic** Spécifie le mode batch. Le **CursorLocation** qui peut affecter les propriété **LockType** paramètres sont disponibles. Par exemple, le **adLockPessimistic** paramètre n’est pas pris en charge si le **CursorLocation** propriété est définie sur **adUseClient**.  
  
 Dans ce mode, chaque appel de la **mise à jour** méthode propage les modifications apportées à la source de données. En mode batch, chaque appel de **mise à jour** ou le déplacement de la position de ligne actuelle enregistre les modifications apportées à la mémoire tampon de copie, mais uniquement le **UpdateBatch** méthode propage les modifications apportées à la source de données.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Mise à jour des données](../../../ado/guide/data/updating-data.md)  
  
-   [Persistance des données](../../../ado/guide/data/persisting-data.md)
