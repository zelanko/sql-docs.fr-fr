---
title: Traitement DES déclarations DE MISE À JOUR DE SELECT FOR UPDATE (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308010"
---
# <a name="processing-select-for-update-statements"></a>Traitement des instructions SELECT FOR UPDATE
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 Pour une interopérabilité maximale, les applications devraient générer des ensembles de résultats qui seront mis à jour avec une mise à jour positionnée en exécutant une déclaration **SELECT FOR UPDATE.** Bien que la bibliothèque de curseurs n’en ait pas besoin, la plupart des sources de données qui prennent en charge les énoncés de mise à jour positionnés.  
  
 La bibliothèque de curseurs ignore les colonnes de la clause **FOR UPDATE** d’une déclaration SELECT **FOR UPDATE;** il supprime cette clause avant de transmettre la déclaration au conducteur. Dans la bibliothèque du curseur, l’attribut SQL_ATTR_CONCURRENCY déclaration, ainsi que les restrictions mentionnées dans la section précédente, contrôle si les colonnes d’un ensemble de résultats peuvent être mises à jour.
