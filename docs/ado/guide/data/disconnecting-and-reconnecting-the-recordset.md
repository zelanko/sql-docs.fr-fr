---
title: Déconnexion et reconnexion du Recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9829ddfd7e625941c97bd3b2027c328a1fba93d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925513"
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Déconnexion et reconnexion du recordset
L’une des fonctionnalités les plus puissantes de ADO est la possibilité d’ouvrir un jeu d’enregistrements côté client à partir d’une source de données, puis de déconnecter le Recordset de la source de données. Une fois le jeu d’enregistrements déconnecté, la connexion à la source de données peut être fermée, libérant ainsi les ressources sur le serveur utilisé pour la gérer. Vous pouvez continuer à afficher et modifier les données dans le jeu d’enregistrements pendant qu’il est déconnecté, puis vous reconnecter ultérieurement à la source de données et envoyer vos mises à jour en mode batch.  
  
 Pour déconnecter un jeu d’enregistrements, ouvrez-le avec un emplacement de curseur égal à adUseClient, puis affectez à la propriété ActiveConnection la valeur Nothing. (Les utilisateurs C++ doivent définir le ActiveConnection comme étant égal à NULL pour se déconnecter.)  
  
 Nous utiliserons un jeu d’enregistrements déconnecté plus loin dans cette section quand nous aborderons la persistance des jeux d’enregistrements pour traiter un scénario dans lequel les données d’un jeu d’enregistrements sont disponibles pour une application alors que l’ordinateur client n’est pas connecté à un réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [Mode Batch](../../../ado/guide/data/batch-mode.md)
