---
title: Architecture du XML côté Client et côté serveur (SQLXML 4.0) de mise en forme | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], XML formatting architecture
- SQLOLEDB provider
- client-side XML formatting
- data providers [SQLXML], XML formatting architecture
- SQLNCLI, XML
- server-side XML formatting
- SQL Server Native Client, XML
- SQLXMLOLEDB Provider, XML formatting architecture
ms.assetid: 52440d9e-89fd-4c15-a008-a1ea99f41387
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 44727b39b52b6e863cfb52dc2e4383e84dd77a40
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225369"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Architecture de la mise en forme XML côté client et côté serveur (SQLXML 4.0)
  L'illustration suivante montre l'architecture de la mise en forme XML côté serveur.  
  
 ![Architecture de mise en forme XML côté serveur. ] (../../../database-engine/dev-guide/media/serversidexml.gif "Mise en forme de l’architecture du XML côté serveur.")  
  
 Dans cet exemple, la commande spécifiée sur le client est envoyée au serveur. Le serveur produit un document XML et le retourne au client. Dans ce cas, le serveur possède une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Avec la mise en forme XML côté serveur, vous pouvez utiliser le fournisseur SQLXMLOLEDB ou le fournisseur SQLOLEDB.  Le fournisseur SQLXMLOLEDB utilise Sqlxml4.dll qui est inclus dans SQLXML 4.0. Lorsque vous utilisez le fournisseur SQLOLEDB, vous obtenez par défaut les fonctionnalités SQLXML fournies par Sqlxmlx.dll, inclus avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ou Microsoft Data Access Components (MDAC) 2.6 ou version ultérieure. Pour utiliser Sqlxml4.dll avec SQLOLEDB, vous devez définir la propriété de Version de SQLXML à la valeur « SQLXML.4.0 » sur l’objet de connexion SQLOLEDB. Quel que soit le cas, le serveur produit le document XML et l'envoie au client.  
  
> [!NOTE]  
>  Les requêtes et les codes de mise à jour XPath sont analysés sur le client. Pour bénéficier des fonctionnalités du modèle ou du code de mise à jour XPath dans SQLXML 4.0, utilisez Sqlxml4.dll.  
  
 L'illustration suivante montre l'architecture de la mise en forme XML côté client.  
  
 ![Architecture de mise en forme XML côté client. ] (../../../database-engine/dev-guide/media/clientsidexml.gif "Mise en forme de l’architecture de données XML du côté client.")  
  
 Dans cet exemple, le client utilise le fournisseur SQLXMLOLEDB. Dans la chaîne de connexion, vous devez définir la propriété du fournisseur de données SQLOLEDB. (C'est la seule valeur acceptée dans SQLXML 4.0.) La commande exécutée sur le client est envoyée au serveur. L'ensemble de lignes généré sur le serveur est envoyé au client. La mise en forme du document XML de l'ensemble de lignes est effectuée sur le client.  
  
 Dans SQLXML 4.0, le fournisseur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) ou le fournisseur SQLOLEDB peut être utilisé en tant que fournisseur de données. Vous pouvez éventuellement accéder à n'importe quelle source de données. Tant que la requête retourne un ensemble de lignes unique, la transformation XML peut être appliquée sur le client.  
  
  
