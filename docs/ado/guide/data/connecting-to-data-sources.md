---
title: Connexion aux Sources de données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1fb066b2d75efd1ea1d5974c92ea5c524165f2e7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472675"
---
# <a name="connecting-to-data-sources"></a>Connexion à des sources de données
ADO **connexion** objet représente une session unique avec une source de données, y compris un SGBD, un magasin de fichiers ou un fichier texte délimité par des virgules. Dans le cas d’un système de base de données client/serveur, la connexion ADO peut être une connexion de réseau réelle au serveur.  
  
 Le **connexion** objet prend en charge divers [propriétés et méthodes](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) pour spécifier les configurations de connexion, ouverture et fermeture des connexions, la création et l’exécution de commandes par rapport à la source de données et fournissant des informations sur la conception de la source de données sous-jacente sous la forme d’ensembles de lignes de schéma, etc. Selon les fonctionnalités prises en charge par le fournisseur, certaines collections, les méthodes ou les propriétés d’un **connexion** objet ne peut pas être disponible.  
  
 Vous pouvez vous connecter à une source de données en utilisant un **connexion** de l’objet ou en utilisant un **Recordset** objet.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Utilisation d’un objet Connection](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Utilisation d’un objet Recordset](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Création d’une chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Spécification des propriétés d’une connexion](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Contrôle des Transactions](../../../ado/guide/data/controlling-transactions-ado.md)
