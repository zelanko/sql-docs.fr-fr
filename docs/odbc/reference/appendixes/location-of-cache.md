---
title: Emplacement du Cache | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 645ff6dc68fec7cf332face2fe53a43555887a48
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="location-of-cache"></a>Emplacement du Cache
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 La bibliothèque de curseurs met en cache les données en mémoire et dans les fichiers temporaires Windows®. Cela limite la taille du jeu de résultats que la bibliothèque de curseurs peut traiter uniquement par un espace disque disponible. Un fichier temporaire est utilisé lorsque les données à mettre en cache seraient dépassent la limite de segment si inséré à la fin du cache de bibliothèque de curseur. Au lieu de cela, les données à mettre en cache sont ajoutées à la place le bloc du dernier enregistrement de données dans le cache. Le bloc du dernier enregistrement de données est enregistré dans un fichier temporaire. Si la bibliothèque de curseurs s’est terminé anormalement, par exemple lorsque la puissance a échoué, il peut laisser des fichiers temporaires de Windows sur le disque. Ceux-ci sont nommés ~ CTT*nnnn*.tmp et sont créés dans le répertoire actif.  
  
> [!NOTE]  
>  Si la bibliothèque de curseurs dans Microsoft® WindowsNT®/Windows2000 tente de cache des données dans un fichier temporaire dans le répertoire actif pendant l’exécution de l’application à partir d’un partage en lecture seule ou un disque compact (par exemple, un exemple de bibliothèque Microsoft Foundation Class), valeur SQLSTATE HY000 (général Error-Unable pour créer une mémoire tampon de fichier) est retourné.

