---
description: Connexion à des sources de données
title: Connexion à des sources de données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: rothja
ms.author: jroth
ms.openlocfilehash: 988eef3a3eb706480e50f0feb6d2fe363b4faabd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991520"
---
# <a name="connecting-to-data-sources"></a>Connexion à des sources de données
Un objet de **connexion** ADO représente une session unique avec une source de données, y compris un SGBD, un magasin de fichiers ou un fichier texte délimité par des virgules. Dans le cas d’un système de base de données client/serveur, la connexion ADO peut être une véritable connexion réseau au serveur.  
  
 L’objet de **connexion** prend en charge différentes [Propriétés et méthodes](../../reference/ado-api/connection-object-properties-methods-and-events.md) pour spécifier des configurations de connexion, ouvrir et fermer des connexions, créer et exécuter des commandes sur la source de données et fournir des informations sur la conception de la source de données sous-jacente sous la forme d’ensembles de lignes de schéma, etc. Selon les fonctionnalités prises en charge par le fournisseur, certaines collections, méthodes ou propriétés d’un objet de **connexion** peuvent ne pas être disponibles.  
  
 Vous pouvez vous connecter à une source de données soit à l’aide d’un objet de **connexion** , soit à l’aide d’un objet **Recordset** .  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisation d’un objet Connection](./using-a-connection-object.md)  
  
-   [Utilisation d’un objet Recordset](./using-a-recordset-object.md)  
  
-   [Création d’une chaîne de connexion](./creating-a-connection-string.md)  
  
-   [Spécification des propriétés d’une connexion](./specifying-connection-properties.md)  
  
-   [Contrôle des transactions](./controlling-transactions-ado.md)