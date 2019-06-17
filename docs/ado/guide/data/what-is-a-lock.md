---
title: Qu’est qu’un verrou ? | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 59234b24d7a3e07c1d6500c41dd0ec2a16f95ee1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718374"
---
# <a name="what-is-a-lock"></a>Qu’est qu’un verrou ?
Le verrouillage est le processus par lequel un SGBD limite l’accès à une ligne dans un environnement multi-utilisateur. Lorsqu’une ligne ou une colonne est verrouillée exclusivement, les autres utilisateurs ne sont pas autorisés à accéder aux données verrouillées jusqu'à ce que le verrou est libéré. Cela garantit que deux utilisateurs ne peuvent pas mettre à jour simultanément la même colonne dans une ligne.  
  
 Les verrous peuvent s’avérer très coûteuses du point de vue de la ressource et doivent être utilisés uniquement lorsque nécessaire pour préserver l’intégrité des données. Dans une base de données où des centaines voire des milliers d’utilisateurs essaie d’accéder à un enregistrement de chaque seconde - comme une base de données connecté à Internet - inutiles donc baisse des performances dans votre application.  
  
 Vous pouvez contrôler la façon dont la source de données et la bibliothèque de curseurs ADO gérer l’accès concurrentiel en choisissant l’option de verrouillage appropriée.  
  
 Définir le **LockType** propriété avant d’ouvrir un **Recordset** pour spécifier le type de verrouillage le fournisseur doit utiliser pour l’ouvrir. Lire la propriété pour retourner le type de verrouillage en cours d’utilisation sur une ouverte **Recordset** objet.  
  
 Les fournisseurs ne peuvent pas en charge tous les types de verrous. Si un fournisseur ne peut pas prendre en charge demandé **LockType** définition, elle remplacera un autre type de verrouillage. Pour déterminer les fonctionnalités de verrouillage disponibles dans un **Recordset** de l’objet, utilisez le [prend en charge](../../../ado/reference/ado-api/supports-method.md) méthode avec **adUpdate** et **adUpdateBatch**.  
  
 Le **adLockPessimistic** paramètre n’est pas pris en charge si le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété est définie sur **adUseClient.** Si une valeur non pris en charge est définie, aucune erreur ne se produit ; prise en charge la plus proche **LockType** sera utilisé à la place.  
  
 Le **LockType** propriété est en lecture/écriture lors de la **Recordset** est fermé et en lecture seule lorsqu’il est ouvert.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de verrous](../../../ado/guide/data/types-of-locks.md)
