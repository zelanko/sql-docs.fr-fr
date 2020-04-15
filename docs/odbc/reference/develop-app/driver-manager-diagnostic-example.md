---
title: Exemple diagnostique de gestionnaire de conducteur (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 839095e5544cab73cdddd4f4b17a3d8d52136c9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305810"
---
# <a name="driver-manager-diagnostic-example"></a>Exemple de diagnostic du gestionnaire de pilotes
Le Driver Manager peut également générer des messages diagnostiques. Par exemple, si une demande a passé une option de direction invalide à **SQLDataSources**, le gestionnaire de conducteur peut formater et retourner les valeurs suivantes de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Parce que l’erreur s’est produite dans le Driver Manager, il a ajouté des préfixes au message diagnostique pour son fournisseur ([Microsoft]) et son identifiant ([ODBC Driver Manager]).
