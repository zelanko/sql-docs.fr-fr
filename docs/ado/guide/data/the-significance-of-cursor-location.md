---
title: L’importance de l’emplacement du curseur | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- server-side cursors [ADO]
- cursors [ADO], client-side
- client-side cursors [ADO]
- cursors [ADO], server-side
ms.assetid: 70ef5b1c-0459-41a1-b796-031f61a29a8a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e663ac5cdcf85fc1d050e0f066b597d29141ebfd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923891"
---
# <a name="the-significance-of-cursor-location"></a>Signification de l’emplacement du curseur
Chaque curseur utilise des ressources temporaires pour contenir ses données. Ces ressources peuvent être en mémoire, un fichier d’échange de disque, les fichiers de disque temporaire ou même temporaire dans la base de données. Le curseur est appelé un *côté client* curseur lorsque ces ressources sont situés sur l’ordinateur client. Le curseur est appelé un *côté serveur* curseur lorsque ces ressources sont situés sur le serveur.  
  
## <a name="client-side-cursors"></a>Curseurs côté client  
 Dans ADO, appelez un curseur côté client en utilisant le **adUseClient CursorLocationEnum.** Avec un curseur côté client non keyset, le serveur envoie l’ensemble de résultats sur le réseau à l’ordinateur client. L’ordinateur client fournit et gère les ressources temporaires requises par le curseur et jeu de résultats. L’application côté client peut parcourir l’ensemble de résultats pour déterminer les lignes requises.  
  
 Statiques et pilotés par les curseurs côté client peuvent placer une charge importante sur votre station de travail si elles comprennent trop de lignes. Alors que toutes les bibliothèques de curseur sont capables de créer des curseurs avec des milliers de lignes, les applications conçues pour extraire ces ensembles de lignes volumineux peuvent être lent. Il existe des exceptions, bien sûr. Pour certaines applications, un curseur côté client volumineux peut être parfaitement approprié et performances ne soient pas un problème.  
  
 L’un des avantages évidents du curseur côté client sont une réponse rapide. Une fois que le jeu de résultats a été téléchargé sur l’ordinateur client, la navigation des lignes est très rapide. Votre application est généralement plus évolutive avec les curseurs côté client, car les besoins en ressources du curseur sont placés sur chaque client et non sur le serveur.  
  
## <a name="server-side-cursors"></a>Curseurs côté serveur  
 Dans ADO, appelez un curseur côté serveur en utilisant le **adUseServer CursorLocationEnum.** Avec un curseur côté serveur, le serveur gère le résultat défini à l’aide des ressources fournies par l’ordinateur du serveur. Le curseur côté serveur retourne uniquement les données demandées sur le réseau. Ce type de curseur peut parfois offrir de meilleures performances que le curseur côté client, en particulier dans les situations où un trafic réseau excessif est un problème.  
  
 Toutefois, il est important de souligner qu’un curseur côté serveur consomme - au moins temporairement - importantes ressources du serveur pour chaque client actif. Vous devez planifier en conséquence pour vous assurer que votre matériel serveur est capable de gérer tous les curseurs côté serveur demandées par les clients actifs. En outre, un curseur côté serveur peut être lent, car il fournit un accès de ligne unique uniquement - aucun curseur de lot n’est disponible.  
  
 Les curseurs côté serveur sont utiles lors de l’insertion, la mise à jour ou suppression d’enregistrements. Avec les curseurs côté serveur, vous pouvez avoir plusieurs instructions actives sur la même connexion.
