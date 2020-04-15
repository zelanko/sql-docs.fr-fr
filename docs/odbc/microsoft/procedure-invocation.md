---
title: Procédure d’invocation (en anglais) Microsoft Docs
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
ms.openlocfilehash: 32617cdb753f5fc1b9c52520cb609d2902137b54
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290770"
---
# <a name="procedure-invocation"></a>Appel de procédure
Lorsque le pilote Microsoft Access est utilisé, les procédures peuvent être invoquées par le conducteur en utilisant la fonction **SQLExecDirect** ou*parameter* **SQLPrepare** avec la syntaxe suivante : 'CALL *procedure-name* *[(paramètre...).* Notez que les expressions ne sont pas prises en charge comme paramètres d’une procédure appelée.  
  
 Si un nom de procédure inclut un tiret, le nom doit être délimité avec des citations arrière (').  
  
 Une requête paramétrée peut être appelée à l’aide de la déclaration précédente.
