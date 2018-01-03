---
title: "Connexion aux Sources de données | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dafec45c1acbe10277738f809c0804dc298be282
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-to-data-sources"></a>Connexion à des sources de données
ADO **connexion** objet représente une session unique avec une source de données, y compris un SGBD, un magasin de fichiers ou un fichier texte délimité par des virgules. Dans le cas d’un système de base de données client/serveur, la connexion ADO peut être une connexion réseau réelle au serveur.  
  
 Le **connexion** objet prend en charge divers [propriétés et méthodes](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) pour spécifier la configuration des connexions, ouverture et fermeture des connexions, la création et l’exécution de commandes sur la source de données et fournissant des informations sur la conception de la source de données sous-jacente sous la forme d’ensembles de lignes de schéma, etc. Selon les fonctionnalités prises en charge par le fournisseur, certaines collections, des méthodes ou propriétés d’un **connexion** objet n’est peut-être pas disponible.  
  
 Vous pouvez vous connecter à une source de données en utilisant un **connexion** de l’objet ou en utilisant un **Recordset** objet.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Utilisation d’un objet Connection](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Utilisation d’un objet Recordset](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Création d’une chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Spécification des propriétés d’une connexion](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Contrôle des Transactions](../../../ado/guide/data/controlling-transactions-ado.md)
