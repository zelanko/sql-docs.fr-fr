---
title: Traitement des instructions SELECT FOR UPDATE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f54d31426773f294a4a23f059c9f906d430056f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63057019"
---
# <a name="processing-select-for-update-statements"></a>Traitement des instructions SELECT FOR UPDATE
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Pour une interopérabilité maximale, les applications doivent générer des jeux de résultats qui sera mis à jour avec une instruction de mise à jour positionnée en exécutant un **Sélectionnez pour mettre à jour** instruction. Bien que la bibliothèque de curseurs n’a pas cette exigence, il est requis par la plupart des sources de données qui prennent en charge les instructions de mise à jour positionnée.  
  
 La bibliothèque de curseurs ignore les colonnes dans le **pour la mise à jour** clause d’une **SELECT FOR UPDATE** instruction ; il supprime cette clause avant de transmettre l’instruction au pilote. Dans la bibliothèque de curseurs, l’attribut d’instruction SQL_ATTR_CONCURRENCY, ainsi que les restrictions mentionnées dans la section précédente, contrôles si les colonnes dans un résultat de la valeur peuvent être mis à jour.
