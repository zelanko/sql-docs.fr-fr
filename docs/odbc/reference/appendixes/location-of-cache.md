---
title: Emplacement de cache (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 13510332ae8bfab07a13d7831f9f74a048551214
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288617"
---
# <a name="location-of-cache"></a>Emplacement du cache
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser la fonctionnalité du curseur du conducteur.  
  
 La bibliothèque de curseurs cache des données dans la mémoire et dans Windows® des fichiers temporaires. Cela limite la taille de l’ensemble de résultat que la bibliothèque de curseurs ne peut gérer que par l’espace disque disponible. Un fichier temporaire est utilisé lorsque les données à mettre en cache traverseraient la limite du segment si elles sont insérées à l’extrémité du cache de la bibliothèque du curseur. Au lieu de cela, les données à mettre en cache sont ajoutées à la place du dernier bloc de données enregistrés dans le cache. Le dernier bloc de données enregistré est enregistré dans un fichier temporaire. Si la bibliothèque de curseurs se termine anormalement, par exemple lorsque la puissance tombe en panne, elle peut laisser des fichiers temporaires Windows sur le disque. Ceux-ci sont nommés 'CTT*nnnn*.tmp et sont créés dans le répertoire actuel.  
  
> [!NOTE]  
>  Si la bibliothèque de curseurs de Microsoft® WindowsNT®/Windows2000 tente de mettre en cache des données dans un fichier temporaire sur le répertoire actuel pendant que l’application est en cours d’exécution à partir d’une part de lecture seulement ou d’un disque compact (comme un échantillon microsoft Foundation Class Library), SQLSTATE HY000 (General Error-Unable pour créer un mémoire) sera retourné.
