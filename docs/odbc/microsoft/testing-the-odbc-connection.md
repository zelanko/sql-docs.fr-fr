---
title: Test de la connexion ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 543ab436ac7dca5e0d5965220cd90a798afb5ccf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633174"
---
# <a name="testing-the-odbc-connection"></a>Test de la connexion ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Lors de la résolution des problèmes d’accès ODBC pour Oracle 7.x et les serveurs Oracle8 SGBDR, il peut être nécessaire vérifier que le SQL sous-jacent * Net et adaptateurs de protocole Oracle sont correctement installés. Pour ce faire, utilisez l’utilitaire fourni par Oracle Nettest.exe dans le répertoire Orawin\Bin.  
  
 Nettest est un utilitaire simple qui tente de se connecter au serveur sélectionné en utilisant uniquement l’installé SQL * Net des logiciels qui font partie du client Oracle. L’utilitaire vous demandera un nom de connexion, mot de passe et TNS chaîne de connexion. Si le client Oracle est installé correctement, l’utilitaire affiche simplement « Ping réussi. » Si la connexion n’a pas réussie, vous devez consulter un administrateur de base de données.
