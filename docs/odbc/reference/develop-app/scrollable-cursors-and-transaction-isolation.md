---
title: Curseurs avec défilement et Isolation des transactions | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5510eb58315f70195eb40390edec1766c350fb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662347"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Curseurs avec défilement et isolation des transactions
Le tableau suivant répertorie les facteurs régissant la visibilité des modifications.  
  
|Modifications apportées par :|Visibilité dépend de :|  
|----------------------|----------------------------|  
|Curseur|Type de curseur, implémentation des curseurs|  
|Autres instructions dans la même transaction|Type de curseur|  
|Instructions dans d’autres transactions|Type de curseur, niveau d’isolation de transaction|  
  
 Ces facteurs sont affichés dans l’illustration suivante.  
  
 ![Facteurs régissant la visibilité des modifications](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 Le tableau suivant récapitule la capacité de chaque type de curseur à détecter les modifications apportées par lui-même, par d’autres opérations dans sa propre transaction et par d’autres transactions. La visibilité des modifications de ce dernier varie selon le type de curseur et le niveau d’isolation de la transaction contenant le curseur.  
  
|Curseur type\action|Self|Propriétaire<br /><br /> BeginTransaction|Dépendant<br /><br /> BeginTransaction<br /><br /> (RU[a])|Dépendant<br /><br /> BeginTransaction<br /><br /> (RC[a])|Dépendant<br /><br /> BeginTransaction<br /><br /> (RR[a])|Dépendant<br /><br /> BeginTransaction<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Statique|||||||  
|Insert|Peut-être [b]|non|non|non|non|non|  
|Update|Peut-être [b]|non|non|non|non|non|  
|DELETE|Peut-être [b]|non|non|non|non|non|  
|Curseur piloté par jeu de clés|||||||  
|Insert|Peut-être [b]|non|non|non|non|non|  
|Update|Oui|Oui|Oui|Oui|non|non|  
|DELETE|Peut-être [b]|Oui|Oui|Oui|non|non|  
|Dynamique|||||||  
|Insert|Oui|Oui|Oui|Oui|Oui|non|  
|Update|Oui|Oui|Oui|Oui|non|non|  
|DELETE|Oui|Oui|Oui|Oui|non|non|  
  
 [a] les lettres entre parenthèses indiquent le niveau d’isolation de la transaction contenant le curseur ; le niveau d’isolation de l’autre transaction (dans lequel la modification apportée) n’est pas pertinent.  
  
 RU : Lecture non validée  
  
 RC : Lecture validée  
  
 RR : Lecture renouvelée  
  
 %S : sérialisable  
  
 [b] varie selon la façon dont le curseur est implémenté. Indique si le curseur peut détecter ces modifications est signalé via l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.
