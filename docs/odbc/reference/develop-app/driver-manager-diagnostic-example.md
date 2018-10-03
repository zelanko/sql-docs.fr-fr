---
title: Exemple de Diagnostic du Gestionnaire de pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ad253c2d0603846d6d1f795f6115e7bb727b3da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47778575"
---
# <a name="driver-manager-diagnostic-example"></a>Exemple de diagnostic du gestionnaire de pilotes
Le Gestionnaire de pilotes peut également générer des messages de diagnostic. Par exemple, si une application a passé une option direction non valide pour **SQLDataSources**, le Gestionnaire de pilotes peut mettre en forme et retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Étant donné que l’erreur s’est produite dans le Gestionnaire de pilotes, il ajouté préfixes pour le message de diagnostic pour son fournisseur ([Microsoft]) et de son identificateur ([Gestionnaire de pilotes ODBC]).
