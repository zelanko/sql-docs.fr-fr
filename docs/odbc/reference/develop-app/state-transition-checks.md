---
title: Contrôles de transition de l’État (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dc1ddc126a2d652dfdb038cbb0e510f9735d7b0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299704"
---
# <a name="state-transition-checks"></a>Vérifications des transitions d’état
Le gestionnaire de conducteur vérifie que l’état de l’environnement, de la connexion ou de la déclaration est approprié pour la fonction appelée. Par exemple, une connexion doit être dans un état attribué lorsque **SQLConnect** est appelé; une déclaration doit être dans un état préparé lorsque **SQLExecute** est appelé. Le Driver Manager retourne SQL_ERROR pour les erreurs de transition de l’État.
