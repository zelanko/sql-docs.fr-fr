---
title: Cursors défilementables et isolement des transactions (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e40278bd209132736aee2788b5648ffa84a44e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304220"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Curseurs avec défilement et isolation des transactions
Le tableau suivant énumère les facteurs régissant la visibilité des changements.  
  
|Modifications apportées par :|La visibilité dépend de :|  
|----------------------|----------------------------|  
|Curseur|Type de curseur, implémentation de curseur|  
|Autres relevés dans la même transaction|Type de curseur|  
|Déclarations dans d’autres transactions|Type de curseur, niveau d’isolement des transactions|  
  
 Ces facteurs sont indiqués dans l’illustration suivante.  
  
 ![Facteurs régissant la visibilité des changements](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 Le tableau suivant résume la capacité de chaque type de curseur à détecter les changements apportés par lui-même, par d’autres opérations dans sa propre transaction, et par d’autres transactions. La visibilité de ces derniers changements dépend du type de curseur et du niveau d’isolement de la transaction contenant le curseur.  
  
|Type curseur|Self|Propre<br /><br /> Txn|Othr Othr<br /><br /> Txn<br /><br /> (RU[a])|Othr Othr<br /><br /> Txn<br /><br /> (RC[a])|Othr Othr<br /><br /> Txn<br /><br /> (RR[a])|Othr Othr<br /><br /> Txn<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|statique|||||||  
|Insérer|Peut-être[b]|Non|Non|Non|Non|Non|  
|Update|Peut-être[b]|Non|Non|Non|Non|Non|  
|DELETE|Peut-être[b]|Non|Non|Non|Non|Non|  
|Curseur piloté par jeu de clés|||||||  
|Insérer|Peut-être[b]|Non|Non|Non|Non|Non|  
|Update|Oui|Oui|Oui|Oui|Non|Non|  
|DELETE|Peut-être[b]|Oui|Oui|Oui|Non|Non|  
|Dynamique|||||||  
|Insérer|Oui|Oui|Oui|Oui|Oui|Non|  
|Update|Oui|Oui|Oui|Oui|Non|Non|  
|DELETE|Oui|Oui|Oui|Oui|Non|Non|  
  
 [a] Les lettres entre parenthèses indiquent le niveau d’isolement de la transaction contenant le curseur; le niveau d’isolement de l’autre transaction (dans lequel la modification a été apportée) n’est pas pertinent.  
  
 RU: Lire non engagé  
  
 RC: Lire engagé  
  
 RR: Lecture répétable  
  
 S: Serializable  
  
 [b] Dépend de la façon dont le curseur est mis en œuvre. La question de savoir si le curseur peut détecter de tels changements est signalée par l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.
