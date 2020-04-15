---
title: Connexion directe aux conducteurs . Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLDriverConnect function [ODBC], connecting directly to drivers
- connecting to driver [ODBC], drivers
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6aacb5d3df985949e04cdd47a9fe460cddbde6a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299079"
---
# <a name="connecting-directly-to-drivers"></a>Connexion directe à des pilotes
Comme cela a été discuté dans [Choisir une source de données ou un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md), plus tôt dans cette section, certaines applications ne veulent pas utiliser une source de données du tout. Au lieu de cela, ils veulent se connecter directement à un conducteur. **SQLDriverConnect** fournit un moyen pour l’application de se connecter directement à un pilote sans spécifier une source de données. Conceptuellement, une source de données temporaire est créée au moment de l’exécution.  
  
 Pour se connecter directement à un pilote, l’application spécifie le mot clé **DRIVER** dans la chaîne de connexion au lieu du mot clé **DSN.** La valeur du mot clé **DRIVER** est la description du conducteur tel que retourné par **SQLDrivers**. Supposons, par exemple, qu’un pilote ait la description paradoxal et qu’il exige le nom d’un répertoire contenant les fichiers de données. Pour se connecter à ce pilote, l’application peut utiliser l’une ou l’autre des chaînes de connexion suivantes :  
  
```  
DRIVER={Paradox Driver};Directory=C:\PARADOX;  
DRIVER={Paradox Driver};  
```  
  
 Avec la première chaîne, le conducteur n’aurait pas besoin d’informations supplémentaires. Avec la deuxième chaîne, le conducteur devrait demander le nom de l’annuaire contenant les fichiers de données.
