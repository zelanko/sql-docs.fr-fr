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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 904028cd7b3798fcac8f9e5afa6186fae3e9fa29
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81308010"
---
# <a name="processing-select-for-update-statements"></a>Traitement des instructions SELECT FOR UPDATE
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 Pour une interopérabilité maximale, les applications doivent générer des jeux de résultats qui seront mis à jour avec une instruction de mise à jour positionnée en exécutant une instruction **Select for Update** . Même si la bibliothèque de curseurs n’en a pas besoin, elle est requise par la plupart des sources de données qui prennent en charge les instructions de mise à jour positionnée.  
  
 La bibliothèque de curseurs ignore les colonnes de la clause **for Update** d’une instruction **Select for Update** . elle supprime cette clause avant de passer l’instruction au pilote. Dans la bibliothèque de curseurs, l’attribut d’instruction SQL_ATTR_CONCURRENCY, ainsi que les restrictions mentionnées dans la section précédente, contrôlent si les colonnes d’un jeu de résultats peuvent être mises à jour.
