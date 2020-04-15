---
title: Vérifications d’erreur et d’avertissement du gestionnaire de conducteur (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee8a0f5ebfac8b6f87281806f07989f4980eb9b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305781"
---
# <a name="driver-manager-error-and-warning-checks"></a>Vérifications des erreurs et avertissements du gestionnaire de pilotes
Le Gestionnaire de pilote implémente complètement ou partiellement un certain nombre de fonctions et vérifie donc la totalité ou certaines des erreurs et avertissements dans ces fonctions.  
  
-   Le Gestionnaire de chauffeur met en œuvre **SQLDataSources** et **SQLDrivers** et vérifie toutes les erreurs et avertissements dans ces fonctions.  
  
-   Le gestionnaire de conducteur vérifie si un conducteur met en œuvre **SQLGetFunctions**. Si le conducteur ne met pas en œuvre **SQLGetFunctions**, le Gestionnaire de conducteur met en œuvre et vérifie toutes les erreurs et avertissements qui s’y y multiplient.  
  
-   Le Gestionnaire de chauffeur implémente partiellement **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**, **SQLFreeHandle**, **SQLGetDiagRec**, et **SQLGetDiagField** et vérifie certaines erreurs dans ces fonctions. Il peut renvoyer les mêmes erreurs que le conducteur pour certaines de ces fonctions parce que les deux effectuent des opérations similaires. Par exemple, le gestionnaire de conducteur ou le conducteur peut retourner SQLSTATE IM008 (Dialog a échoué) si l’un ou l’autre est incapable d’afficher une boîte de dialogue de connexion pour **SQLDriverConnect**.
