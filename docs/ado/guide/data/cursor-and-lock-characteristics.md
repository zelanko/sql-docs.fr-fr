---
title: Curseur et les caractéristiques de verrou | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a3a206a21cf7c6680a656c89c48b8f52d1069d78
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702116"
---
# <a name="cursor-and-lock-characteristics"></a>Caractéristiques des curseurs et des verrous
Bien que les caractéristiques d’un curseur dépendent des fonctionnalités du fournisseur, les avantages et inconvénients suivants s’appliquent généralement aux différents types de curseurs et des verrous.  
  
|Type de curseur ou de verrou|Avantages|Inconvénients|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-Besoins en ressources faible|-Impossible de faire défiler vers l’arrière<br />-Aucun accès concurrentiel aux données|  
|**adOpenStatic**|-Avec défilement|-Aucun accès concurrentiel aux données|  
|**adOpenKeyset**|-Certains accès concurrentiel aux données<br />-Avec défilement|-Besoins en ressources supérieur<br />-Non disponible dans un scénario déconnecté|  
|**adOpenDynamic**|-Accès concurrentiel aux données haute<br />-Avec défilement|-Besoins en ressources le plus élevés<br />-Non disponible dans un scénario déconnecté|  
|**adLockReadOnly**|-Besoins en ressources faible<br />-Hautement évolutif|-À jour des données via un curseur|  
|**adLockBatchOptimistic**|-   Batch updates<br />-Autorise des scénarios déconnectés<br />-Autres utilisateurs en mesure d’accéder aux données|-Les données peuvent être modifiées par plusieurs utilisateurs à la fois|  
|**adLockPessimistic**|-Les données ne peut pas être modifiées par d’autres utilisateurs lors du verrouillage|: Empêche les autres utilisateurs d’accéder aux données lors du verrouillage|  
|**adLockOptimistic**|-Autres utilisateurs en mesure d’accéder aux données|-Les données peuvent être modifiées par plusieurs utilisateurs à la fois|
