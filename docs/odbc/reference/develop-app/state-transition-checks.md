---
title: Vérifications de la transition d’État | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b337d317092ad6ae20cc91236d69c1314de96bce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107285"
---
# <a name="state-transition-checks"></a>Vérifications des transitions d’état
Le gestionnaire de pilotes vérifie que l’état de l’environnement, de la connexion ou de l’instruction est approprié pour la fonction appelée. Par exemple, une connexion doit être dans un État alloué lorsque **SQLConnect** est appelé ; une instruction doit être dans un état préparé lorsque **SQLExecute** est appelé. Le gestionnaire de pilotes retourne SQL_ERROR pour les erreurs de transition d’État.
