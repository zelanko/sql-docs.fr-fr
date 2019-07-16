---
title: La mise à jour des données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], about data updates
- updating data [ADO], about updating data
ms.assetid: 6508e4e9-e33a-4dad-b340-5d632fd78a91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5bd3b72e897b8ae12441c7cf28d1995eb45318d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923692"
---
# <a name="updating-data"></a>Mise à jour des données
Comportement de mise à jour et les fonctionnalités dépend en grande partie mettre à jour le mode (type de verrou), type de curseur et l’emplacement du curseur.  
  
 Utilisez le **mise à jour** méthode pour enregistrer les modifications apportées à l’enregistrement en cours d’un **Recordset** objet depuis l’appel la **AddNew** (méthode) ou parce que la modification des valeurs de champs dans un enregistrement existant. Le **Recordset** objet doit prendre en charge les mises à jour.  
  
 Si le **Recordset** objet prend en charge la mise à jour par lot, vous pouvez mettre en cache plusieurs modifications à un ou plusieurs enregistrements localement jusqu'à ce que vous appeliez la **UpdateBatch** (méthode). Si vous modifiez l’enregistrement en cours ou ajouter un nouvel enregistrement lorsque vous appelez le **UpdateBatch** (méthode), ADO appelle automatiquement la **mise à jour** méthode pour enregistrer les modifications en attente dans l’enregistrement en cours avant transmettre les modifications par lot au fournisseur.  
  
 L’enregistrement actif reste actif après avoir appelé la **mise à jour** ou **UpdateBatch** méthodes.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Mode immédiat](../../../ado/guide/data/immediate-mode.md)  
  
-   [Mode batch](../../../ado/guide/data/batch-mode.md)  
  
-   [Traitement des transactions](../../../ado/guide/data/transaction-processing.md)
