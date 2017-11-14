---
title: "Déconnexion et reconnexion de l’ensemble d’enregistrements | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a6ddbc392ae0bd0c378a4d08cd2c76f3119d8332
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Déconnexion et reconnexion de l’ensemble d’enregistrements
Une des fonctionnalités plus puissantes d’ADO est la possibilité d’ouvrir un jeu d’enregistrements côté client à partir d’une source de données et se déconnecter ensuite le jeu d’enregistrements à partir de la source de données. Une fois que le jeu d’enregistrements a été déconnecté, la connexion à la source de données peut être fermée, libérant ainsi les ressources sur le serveur utilisé pour maintenir. Vous pouvez continuer à afficher et modifier les données dans le jeu d’enregistrements pendant qu’il est déconnecté et reconnecter ultérieurement à la source de données et envoyer vos mises à jour en mode batch.  
  
 Pour déconnecter un objet Recordset, ouvrez-le dans un emplacement du curseur d’adUseClient et puis définissez la propriété ActiveConnection à rien. (Les utilisateurs C++ doivent affecter ActiveConnection égal à NULL pour déconnecter.)  
  
 Nous allons utiliser un jeu d’enregistrements déconnecté plus loin dans cette section lorsque nous aborderons la persistance de Recordset un scénario dans lequel nous devons disposer les données dans un jeu d’enregistrements disponible pour une application pendant que l’ordinateur client n’est pas connecté à un réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [En Mode Batch](../../../ado/guide/data/batch-mode.md)

