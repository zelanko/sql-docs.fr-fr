---
title: Mode Manuel-Commit (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a00ff373e374d0940b3e7259eeb01e26b620cae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287873"
---
# <a name="manual-commit-mode"></a>Mode de validation manuelle
*En mode de validation manuelle,* les applications doivent explicitement effectuer des transactions en appelant **SQLEndTran** pour les valider ou les annuler. Il s’agit du mode de transaction normal pour la plupart des bases de données relationnelles.  
  
 Les transactions en ODBC n’ont pas besoin d’être explicitement lancées. Au lieu de cela, une transaction commence implicitement chaque fois que l’application commence à fonctionner sur la base de données. Si la source de données nécessite une ouverture explicite des transactions, le conducteur doit la fournir chaque fois que l’application exécute une déclaration nécessitant une transaction et qu’il n’y a pas de transaction en cours.
