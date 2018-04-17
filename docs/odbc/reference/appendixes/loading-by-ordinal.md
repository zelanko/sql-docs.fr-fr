---
title: Le chargement par Ordinal | Documents Microsoft
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
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33b538dcba0898e11d84920e9b6153da165200d0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="loading-by-ordinal"></a>Chargement par Ordinal
Dans ODBC 2. *x*, le chargement par ordinal pu être effectué pour améliorer les performances du processus de connexion. Une application ODBC 2. *x* pilote exporte une fonction factice avec l’ordinal 199 ; lorsque le Gestionnaire de pilote détecte, il résout les adresses des fonctions ODBC par ordinal, et non par nom. Cette fonctionnalité est toujours pris en charge pour ODBC 2. *x* pilotes mais n’est ne pas pris en charge pour ODBC 3*.x* pilotes.
