---
title: Erreur du Gestionnaire de pilotes et avertissement | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f212af4169b4c0be2a840f6ff8d7310abb40f53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="driver-manager-error-and-warning-checks"></a>Erreur du Gestionnaire de pilotes et des vérifications d’avertissement
Le Gestionnaire de pilotes complètement ou partiellement implémente plusieurs fonctions et par conséquent recherche tout ou partie des erreurs et avertissements dans les fonctions.  
  
-   Le Gestionnaire de pilotes implémente **SQLDataSources** et **SQLDrivers** et les vérifications pour toutes les erreurs et avertissements dans ces fonctions.  
  
-   Le Gestionnaire de pilotes vérifie si un pilote implémente **SQLGetFunctions**. Si le pilote n’implémente pas **SQLGetFunctions**, le Gestionnaire de pilote implémente et recherche toutes les erreurs et avertissements qu’il contient.  
  
-   Le Gestionnaire de pilotes implémente partiellement **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**, **SQLFreeHandle**, **SQLGetDiagRec**, et **SQLGetDiagField** et les vérifications de certaines erreurs de ces fonctions. Elle peut retourner les mêmes erreurs car le pilote pour certaines de ces fonctions, car les deux effectuent des opérations similaires. Par exemple, le Gestionnaire de pilote ou le pilote peut retourner la valeur SQLSTATE IM008 (échoué de la boîte de dialogue) si l’une est impossible d’afficher une boîte de dialogue de connexion pour **SQLDriverConnect**.
