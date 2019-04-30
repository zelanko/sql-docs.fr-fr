---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b33bc399646a6d274c875abd36d53219a2814e1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200520"
---
# <a name="procedure-invocation"></a>Appel de procédure
Lorsque le pilote Microsoft Access est utilisé, les procédures peuvent être appelées à partir du pilote à l’aide de la **SQLExecDirect** ou **SQLPrepare** fonction avec la syntaxe suivante : {appeler *-nom de la procédure*  [(*paramètre*[,*paramètre*]...)]}. Notez que les expressions ne sont pas prises en charge en tant que paramètres à une procédure appelée.  
  
 Si un nom de procédure comprend un tiret, le nom doit être délimité précédent entre guillemets (').  
  
 Une requête paramétrable peut être appelée à l’aide de l’instruction précédente.
