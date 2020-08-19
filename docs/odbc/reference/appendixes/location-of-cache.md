---
description: Emplacement du cache
title: Emplacement du cache | Microsoft Docs
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
ms.openlocfilehash: 29a0c5507c1b8f581d85b0524784f8ccf1695a5f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429621"
---
# <a name="location-of-cache"></a>Emplacement du cache
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 La bibliothèque de curseurs met en cache les données en mémoire et dans les fichiers temporaires Windows®. Cela limite la taille du jeu de résultats que la bibliothèque de curseurs peut gérer uniquement par l’espace disque disponible. Un fichier temporaire est utilisé lorsque les données à mettre en cache franchissent les limites du segment si elles sont insérées à la fin du cache de la bibliothèque de curseurs. Au lieu de cela, les données à mettre en cache sont ajoutées à la place du dernier bloc de données enregistré dans le cache. Le dernier bloc de données enregistré est enregistré dans un fichier temporaire. Si la bibliothèque de curseurs se termine anormalement, par exemple en cas de panne de courant, elle peut conserver les fichiers temporaires Windows sur le disque. Celles-ci sont nommées ~ CTT*nnnn*. tmp et sont créées dans le répertoire actif.  
  
> [!NOTE]  
>  Si la bibliothèque de curseurs dans Microsoft® Windows NT®/Windows2000 tente de mettre en cache des données dans un fichier temporaire sur le répertoire actif pendant que l’application s’exécute à partir d’un partage en lecture seule ou d’un disque compact (tel qu’un exemple bibliothèque MFC (Microsoft Foundation Class)), SQLSTATE HY000 (erreur générale-impossible de créer un tampon de fichier) est retourné.
