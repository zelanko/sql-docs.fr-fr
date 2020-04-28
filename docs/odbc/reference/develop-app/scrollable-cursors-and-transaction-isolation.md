---
title: Curseurs avec défilement et isolation des transactions | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304220"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Curseurs avec défilement et isolation des transactions
Le tableau suivant répertorie les facteurs qui régissent la visibilité des modifications.  
  
|Modifications apportées par :|La visibilité dépend des éléments suivants :|  
|----------------------|----------------------------|  
|Curseur|Type de curseur, implémentation de curseur|  
|Autres instructions dans la même transaction|Type de curseur|  
|Instructions dans d’autres transactions|Type de curseur, niveau d’isolation de la transaction|  
  
 Ces facteurs sont présentés dans l’illustration suivante.  
  
 ![Facteurs régissant la visibilité des changements](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 Le tableau suivant résume la capacité de chaque type de curseur à détecter les modifications effectuées par lui-même, par d’autres opérations dans sa propre transaction et par d’autres transactions. La visibilité de ces dernières modifications dépend du type de curseur et du niveau d’isolement de la transaction contenant le curseur.  
  
|Curseur type\action|Self|Manuellement<br /><br /> TXN|Dépendant<br /><br /> TXN<br /><br /> (RU [a])|Dépendant<br /><br /> TXN<br /><br /> (RC [a])|Dépendant<br /><br /> TXN<br /><br /> (RR [a])|Dépendant<br /><br /> TXN<br /><br /> (S [a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Statique|||||||  
|Insérer|Peut-être [b]|Non|Non|Non|Non|Non|  
|Update|Peut-être [b]|Non|Non|Non|Non|Non|  
|DELETE|Peut-être [b]|Non|Non|Non|Non|Non|  
|Curseur piloté par jeu de clés|||||||  
|Insérer|Peut-être [b]|Non|Non|Non|Non|Non|  
|Update|Oui|Oui|Oui|Oui|Non|Non|  
|DELETE|Peut-être [b]|Oui|Oui|Oui|Non|Non|  
|Dynamique|||||||  
|Insérer|Oui|Oui|Oui|Oui|Oui|Non|  
|Update|Oui|Oui|Oui|Oui|Non|Non|  
|DELETE|Oui|Oui|Oui|Oui|Non|Non|  
  
 [a] les lettres entre parenthèses indiquent le niveau d’isolement de la transaction contenant le curseur ; le niveau d’isolation de l’autre transaction (dans laquelle la modification a été apportée) n’est pas pertinent.  
  
 RU : lecture non validée  
  
 RC : lecture validée  
  
 RR : lecture renouvelable  
  
 S : sérialisable  
  
 [b] dépend de la façon dont le curseur est implémenté. Si le curseur peut détecter de telles modifications est signalé par le biais de l’option SQL_STATIC_SENSITIVITY dans **SQLGetInfo**.
