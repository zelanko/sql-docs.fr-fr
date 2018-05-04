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
ms.topic: conceptual
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
ms.openlocfilehash: ca642308b52f52eda4f18f467ae70413ba7f3c04
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="cursor-library-operations"></a>Opérations de bibliothèque de curseur
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans tout nouveau développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande d’utiliser les fonctionnalités de curseur du pilote.  
  
 Si une application utilisant une API ODBC 2 *.x* pilote appelle le ODBC 3. *x* bibliothèque de curseurs, l’application peut être en mesure d’utiliser ODBC 3. *x* les fonctionnalités qui ne sont pas pris en charge par ODBC 2 *.x* pilote. Writer de l’application doit veiller comment ces fonctionnalités sont utilisées, toutefois. Utilisation d’ODBC 3. *x* bibliothèque de curseurs n’apporte une ODBC 2 *.x* pilote dans un ODBC 3. *x* pilote.
