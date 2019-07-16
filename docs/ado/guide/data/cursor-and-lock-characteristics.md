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
ms.openlocfilehash: c4d6f86539e1abc7ee74087b130e0186322346e8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925678"
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
|**adLockBatchOptimistic**|-Mises à jour batch<br />-Autorise des scénarios déconnectés<br />-Autres utilisateurs en mesure d’accéder aux données|-Les données peuvent être modifiées par plusieurs utilisateurs à la fois|  
|**adLockPessimistic**|-Les données ne peut pas être modifiées par d’autres utilisateurs lors du verrouillage|: Empêche les autres utilisateurs d’accéder aux données lors du verrouillage|  
|**adLockOptimistic**|-Autres utilisateurs en mesure d’accéder aux données|-Les données peuvent être modifiées par plusieurs utilisateurs à la fois|
