---
title: Mode de validation manuelle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1952d4185c80a3b49b7742a9dba1f3d8d41a6ca6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667917"
---
# <a name="manual-commit-mode"></a>Mode de validation manuelle
*En mode de validation manuelle,* applications doivent terminer explicitement les transactions en appelant **SQLEndTran** pour les valider ou de les restaurer. C’est le mode de transaction normale pour la plupart des bases de données relationnelles.  
  
 Transactions dans ODBC n’ont pas à être explicitement lancée. Au lieu de cela, une transaction commence implicitement à chaque démarrage de l’application fonctionne sur la base de données. Si la source de données requiert l’émission de la transaction explicite, le pilote doit le fournir chaque fois que l’application exécute une instruction qui requiert une transaction et il n’existe aucune transaction en cours.
