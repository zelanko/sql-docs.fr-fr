---
title: Les opérations de curseur bibliothèque | Documents Microsoft
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
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0bac09cb2b45274a5589c152a5b0e714b71f8dc1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-library-operations"></a>Opérations de bibliothèque de curseur
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Si une application utilisant une API ODBC 2*.x* pilote appelle le ODBC 3. *x* bibliothèque de curseurs, l’application peut être en mesure d’utiliser ODBC 3. *x* les fonctionnalités qui ne sont pas pris en charge par ODBC 2*.x* pilote. Writer de l’application doit veiller comment ces fonctionnalités sont utilisées, toutefois. Utilisation d’ODBC 3. *x* bibliothèque de curseurs n’apporte une ODBC 2*.x* pilote dans un ODBC 3. *x* pilote.
