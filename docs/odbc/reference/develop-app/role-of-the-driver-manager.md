---
title: Rôle du gestionnaire de chauffeurs (fr) Microsoft Docs
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
ms.openlocfilehash: ee3d704ea43125c3cd912a4e67d90bf5d50c733e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304300"
---
# <a name="role-of-the-driver-manager"></a>Rôle du gestionnaire de pilotes
Le gestionnaire de pilote détermine l’ordre final dans lequel retourner les enregistrements d’état qu’il génère. En particulier, il détermine quel dossier a le rang le plus élevé et doit être retourné en premier. Le conducteur est responsable de la commande des dossiers d’état qu’il génère. Si les dossiers d’état sont affichés par le gestionnaire de conducteur et le conducteur, le gestionnaire de conducteur est responsable de leur commande. Pour plus d’informations, voir [Séquence des enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md).  
  
 Le gestionnaire de pilote effectue autant de vérification des erreurs qu’il le peut. Cela permet à chaque pilote de vérifier les mêmes erreurs. Par exemple, si un argument de fonction accepte un nombre discret de valeurs, telles que *l’opération* dans **SQLSetPos**, le gestionnaire de conducteur vérifie que la valeur spécifiée est légale.  
  
 Les sections suivantes décrivent les types de conditions vérifiées par le gestionnaire de conducteur. Ils ne sont pas destinés à être exhaustifs; pour une liste complète des SQLSTATEs le gestionnaire de conducteur revient, voir la section «Diagnostics» de chaque fonction; la description de chaque chèque effectuée par le gestionnaire de conducteur commence par les lettres "(DM)." Voir également les tables de transition de l’État à [l’Annexe B : ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); les erreurs indiquées entre parenthèses sont détectées par le gestionnaire de conducteur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Vérifications de la valeur des arguments](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [Vérifications des transitions d’état](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [Vérifications des erreurs générales](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [Vérifications des erreurs et avertissements du gestionnaire de pilotes](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
