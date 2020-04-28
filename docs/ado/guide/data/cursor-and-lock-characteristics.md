---
title: Caractéristiques des curseurs et des verrous | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925678"
---
# <a name="cursor-and-lock-characteristics"></a>Caractéristiques des curseurs et des verrous
Bien que les caractéristiques d’un curseur dépendent des capacités du fournisseur, les avantages et inconvénients suivants s’appliquent généralement aux différents types de curseurs et de verrous.  
  
|Type de curseur ou de verrou|Avantages|Inconvénients|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-Exigences de ressources insuffisantes|-Impossible de faire défiler vers l’arrière<br />-Pas d’accès concurrentiel aux données|  
|**adOpenStatic**|Avec défilement|-Pas d’accès concurrentiel aux données|  
|**adOpenKeyset**|-Accès concurrentiel aux données<br />Avec défilement|-Exigences de ressources plus élevées<br />-Non disponible dans un scénario déconnecté|  
|**adOpenDynamic**|-Accès concurrentiel aux données élevées<br />Avec défilement|-Exigences de ressources les plus élevées<br />-Non disponible dans un scénario déconnecté|  
|**adLockReadOnly**|-Exigences de ressources insuffisantes<br />-Hautement évolutif|-Les données ne pouvant pas être mises à jour via le curseur|  
|**adLockBatchOptimistic**|-Mises à jour par lot<br />-Autorise les scénarios déconnectés<br />-Autres utilisateurs capables d’accéder aux données|-Les données peuvent être modifiées simultanément par plusieurs utilisateurs|  
|**adLockPessimistic**|-Les données ne peuvent pas être modifiées par d’autres utilisateurs quand elles sont verrouillées|-Empêche les autres utilisateurs d’accéder aux données pendant qu’ils sont verrouillés|  
|**adLockOptimistic**|-Autres utilisateurs capables d’accéder aux données|-Les données peuvent être modifiées simultanément par plusieurs utilisateurs|
