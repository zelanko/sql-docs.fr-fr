---
description: Rôle du gestionnaire de pilotes
title: Rôle du gestionnaire de pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- diagnostic information [ODBC], driver manager error checking
- SQLGetDiagField function [ODBC], driver manager
- SQLGetDiagRec function [ODBC], driver manager
- ODBC driver manager [ODBC]
- diagnostic information [ODBC], SqlGetDiagRec
- driver manager [ODBC], error checking
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f974fe6436173b55f39aced45cc38312221cffaa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465656"
---
# <a name="role-of-the-driver-manager"></a>Rôle du gestionnaire de pilotes
Le gestionnaire de pilotes détermine l’ordre final dans lequel retourner les enregistrements d’État qu’il génère. En particulier, il détermine quel enregistrement a le rang le plus élevé et doit être retourné en premier. Le pilote est chargé de classer les enregistrements d’État qu’il génère. Si les enregistrements d’État sont publiés à la fois par le gestionnaire de pilotes et par le pilote, le gestionnaire de pilotes est chargé de les classer. Pour plus d’informations, consultez [séquence des enregistrements d’État](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Le gestionnaire de pilotes fait autant de vérification des erreurs que possible. Cela évite à tous les pilotes de vérifier les mêmes erreurs. Par exemple, si un argument de fonction accepte un nombre discret de valeurs, telles que l' *opération* dans **SQLSetPos**, le gestionnaire de pilotes vérifie que la valeur spécifiée est légale.  
  
 Les sections suivantes décrivent les types de conditions vérifiées par le gestionnaire de pilotes. Ils ne sont pas destinés à être exhaustifs ; pour obtenir la liste complète des SQLSTATEs retournées par le gestionnaire de pilotes, consultez la section « Diagnostics » de chaque fonction. la description de chaque vérification effectuée par le gestionnaire de pilotes commence par les lettres « (DM) ». Consultez également les tableaux de transition d’État dans [annexe B : tables de transition d’État ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); les erreurs indiquées entre parenthèses sont détectées par le gestionnaire de pilotes.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Vérifications de la valeur des arguments](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Vérifications des transitions d’état](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Vérifications des erreurs générales](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Vérifications des erreurs et avertissements du gestionnaire de pilotes](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
