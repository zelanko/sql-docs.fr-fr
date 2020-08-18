---
description: Vérifications des erreurs et avertissements du gestionnaire de pilotes
title: Vérifications des erreurs et des avertissements du gestionnaire de pilotes | Microsoft Docs
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
ms.openlocfilehash: 99a99e1dfeb6cb6993a6967d5d93748afbd44b83
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483052"
---
# <a name="driver-manager-error-and-warning-checks"></a>Vérifications des erreurs et avertissements du gestionnaire de pilotes
Le gestionnaire de pilotes implémente totalement ou partiellement plusieurs fonctions et vérifie donc la totalité ou une partie des erreurs et des avertissements dans ces fonctions.  
  
-   Le gestionnaire de pilotes implémente **SQLDataSources** et **SQLDrivers** et vérifie la totalité des erreurs et des avertissements dans ces fonctions.  
  
-   Le gestionnaire de pilotes vérifie si un pilote implémente **SQLGetFunctions**. Si le pilote n’implémente pas **SQLGetFunctions**, le gestionnaire de pilotes implémente et vérifie toutes les erreurs et tous les avertissements qu’il contient.  
  
-   Le gestionnaire de pilotes implémente partiellement **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**, **SQLFreeHandle**, **SQLGetDiagRec**et **SQLGetDiagField** et recherche des erreurs dans ces fonctions. Elle peut retourner les mêmes erreurs que le pilote pour certaines de ces fonctions, car elles effectuent toutes les deux des opérations similaires. Par exemple, le gestionnaire de pilotes ou le pilote peut retourner SQLSTATE IM008 (échec de la boîte de dialogue) si l’un ou l’autre ne peut pas afficher une boîte de dialogue de connexion pour **SQLDriverConnect**.
