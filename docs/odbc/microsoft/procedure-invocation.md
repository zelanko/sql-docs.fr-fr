---
description: Appel de procédure
title: Appel de procédure | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2643a36c834b577dfcecdcc81fd938a3a7d1018
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340445"
---
# <a name="procedure-invocation"></a>Appel de procédure
Lorsque le pilote Microsoft Access est utilisé, des procédures peuvent être appelées à partir du pilote à l’aide de la fonction **SQLExecDirect** ou **SQLPrepare** avec la syntaxe suivante : {Call *procedure-Name* [(*paramètre*[,*paramètre*]...)]}. Notez que les expressions ne sont pas prises en charge en tant que paramètres d’une procédure appelée.  
  
 Si un nom de procédure comprend un tiret, le nom doit être délimité par des guillemets (').  
  
 Une requête paramétrable peut être appelée à l’aide de l’instruction précédente.
