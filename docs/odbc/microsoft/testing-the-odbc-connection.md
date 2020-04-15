---
title: Test de la connexion ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8de19af2b50a58eef22ec074a308f86717278a48
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303110"
---
# <a name="testing-the-odbc-connection"></a>Test de la connexion ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Lorsque vous dépannez l’accès d’ODBC aux serveurs Oracle 7.x et Oracle8 RDBMS, il peut être nécessaire de vérifier que les adaptateurs de protocoles SQL-Net et Oracle sous-jacents sont correctement installés. Pour ce faire, utilisez l’utilitaire Nettest.exe fourni par Oracle dans l’annuaire Orawin-Bin.  
  
 Nettest est un utilitaire simple qui tente de se connecter au serveur sélectionné en utilisant uniquement le logiciel SQL-Net installé qui fait partie du client Oracle. L’utilitaire demandera un nom de connexion, un mot de passe et une chaîne de connexion TNS. Si le client Oracle est correctement installé, l’utilitaire affichera simplement "Ping Successful". Si la connexion n’a pas été réussie, vous devrez consulter un administrateur de base de données.
