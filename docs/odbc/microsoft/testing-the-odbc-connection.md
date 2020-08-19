---
description: Test de la connexion ODBC
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61a471af3c5681ca58ca3268ad4512ee80abb9cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421543"
---
# <a name="testing-the-odbc-connection"></a>Test de la connexion ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Lors de la résolution des problèmes d’accès ODBC aux serveurs SGBDR Oracle 7. x et Oracle8, il peut être nécessaire de vérifier que les adaptateurs de protocole SQL * Net et Oracle sous-jacents sont correctement installés. Pour ce faire, utilisez l’utilitaire fourni par Oracle Nettest.exe dans le répertoire Orawin\Bin.  
  
 Nettest est un utilitaire simple qui tente de se connecter au serveur sélectionné en utilisant uniquement le logiciel SQL * Net installé qui fait partie du client Oracle. L’utilitaire vous demandera un nom de connexion, un mot de passe et une chaîne de connexion TNS. Si le client Oracle est correctement installé, l’utilitaire affichera simplement « ping réussi ». Si la connexion a échoué, vous devez consulter un administrateur de base de données.
