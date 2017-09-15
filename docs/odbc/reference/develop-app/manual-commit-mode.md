---
title: Mode de validation manuelle | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a5f9d510d1a92ce8faf4fe29f3274afdba6f83b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="manual-commit-mode"></a>Mode de validation manuelle
*En mode de validation manuelle,* applications doivent terminer explicitement les transactions en appelant **SQLEndTran** pour les valider ou de les restaurer. C’est le mode de transaction normale pour la plupart des bases de données relationnelles.  
  
 Transactions dans ODBC n’ont pas à être initialisé explicitement. Au lieu de cela, une transaction commence implicitement à chaque démarrage de l’application fonctionne sur la base de données. Si la source de données requiert l’émission de la transaction explicite, le pilote doit le fournir chaque fois que l’application exécute une instruction qui requiert une transaction et il n’existe aucune transaction en cours.
