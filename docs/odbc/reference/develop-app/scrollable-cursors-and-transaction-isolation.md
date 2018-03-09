---
title: "Les curseurs permettant le défilement et Isolation des transactions | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6c9e38f4287a8832d8e794940093ce696ac0eaf7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Les curseurs permettant le défilement et Isolation des transactions
Le tableau suivant répertorie les facteurs régissant la visibilité des modifications.  
  
|Modifications apportées par :|Visibilité dépend :|  
|----------------------|----------------------------|  
|Curseur|Type de curseur, implémentation des curseurs|  
|Autres instructions dans la même transaction|Type de curseur|  
|Instructions dans d’autres transactions|Type de curseur, niveau d’isolation de transaction|  
  
 Ces facteurs sont affichés dans l’illustration suivante.  
  
 ![Facteurs régissant la visibilité des modifications](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 Le tableau suivant récapitule la capacité de chaque type de curseur à détecter les modifications apportées par lui-même, par d’autres opérations dans sa propre transaction et par d’autres transactions. La visibilité des modifications de ce dernier varie selon le type de curseur et le niveau d’isolation de la transaction contenant le curseur.  
  
|Curseur type\action|Self|Propriétaire<br /><br /> Transactions-dépassement|Dépendant<br /><br /> Transactions-dépassement<br /><br /> (RU[a])|Dépendant<br /><br /> Transactions-dépassement<br /><br /> (RC[a])|Dépendant<br /><br /> Transactions-dépassement<br /><br /> (RR[a])|Dépendant<br /><br /> Transactions-dépassement<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Statique|||||||  
|Insert|Maybe [b]|non|non|non|non|non|  
|Update|Maybe [b]|non|non|non|non|non|  
|DELETE|Maybe [b]|non|non|non|non|non|  
|Curseur piloté par jeu de clés|||||||  
|Insert|Maybe [b]|non|non|non|non|non|  
|Update|Oui|Oui|Oui|Oui|non|non|  
|DELETE|Maybe [b]|Oui|Oui|Oui|non|non|  
|Dynamique|||||||  
|Insert|Oui|Oui|Oui|Oui|Oui|non|  
|Update|Oui|Oui|Oui|Oui|non|non|  
|DELETE|Oui|Oui|Oui|Oui|non|non|  
  
 [a] les lettres entre parenthèses indiquent le niveau d’isolation de la transaction contenant le curseur ; le niveau d’isolation de l’autre transaction (dans lequel la modification a été apportée) n’est pas pertinent.  
  
 RU : La lecture non validée  
  
 RC : Lecture validée  
  
 L’enregistrement de ressource : Lecture renouvelable  
  
 %S : sérialisable  
  
 [b] dépend de comment le curseur est implémenté. Indique si le curseur peut détecter ces modifications est signalé via l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.
