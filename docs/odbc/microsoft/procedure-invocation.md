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
ms.openlocfilehash: bc37ef6d268dba71f8270909ea9c5b938ef3ee75
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070494"
---
# <a name="procedure-invocation"></a>Appel de procédure
Lorsque le pilote Microsoft Access est utilisé, des procédures peuvent être appelées à partir du pilote à l’aide de la fonction **SQLExecDirect** ou **SQLPrepare** avec la syntaxe suivante : {Call *procedure-Name* [(*paramètre*[,*paramètre*]...)]}. Notez que les expressions ne sont pas prises en charge en tant que paramètres d’une procédure appelée.  
  
 Si un nom de procédure comprend un tiret, le nom doit être délimité par des guillemets (').  
  
 Une requête paramétrable peut être appelée à l’aide de l’instruction précédente.
