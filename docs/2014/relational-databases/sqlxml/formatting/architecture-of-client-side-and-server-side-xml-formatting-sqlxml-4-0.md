---
title: Architecture de la mise en forme XML côté client et côté serveur (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03601c4d36a3e11de4df35bc32237ac554ca93fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014441"
---
# <a name="architecture-of-client-side-and-server-side-xml-formatting-sqlxml-40"></a>Architecture de la mise en forme XML côté client et côté serveur (SQLXML 4.0)
  L'illustration suivante montre l'architecture de la mise en forme XML côté serveur.  
  
 ![Architecture de mise en forme XML côté serveur.](../../../database-engine/dev-guide/media/serversidexml.gif "Architecture de mise en forme XML côté serveur.")  
  
 Dans cet exemple, la commande spécifiée sur le client est envoyée au serveur. Le serveur produit un document XML et le retourne au client. Dans ce cas, le serveur dispose d’une instance [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]de. Avec la mise en forme XML côté serveur, vous pouvez utiliser le fournisseur SQLXMLOLEDB ou le fournisseur SQLOLEDB.  Le fournisseur SQLXMLOLEDB utilise Sqlxml4.dll qui est inclus dans SQLXML 4.0. Lorsque vous utilisez le fournisseur SQLOLEDB, vous obtenez par défaut les fonctionnalités SQLXML fournies par Sqlxmlx.dll, inclus avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows ou Microsoft Data Access Components (MDAC) 2.6 ou version ultérieure. Pour utiliser Sqlxml4. dll avec SQLOLEDB, vous devez définir la propriété de version SQLXML sur « SQLXML. 4.0 » sur l’objet de connexion SQLOLEDB. Quel que soit le cas, le serveur produit le document XML et l'envoie au client.  
  
> [!NOTE]  
>  Les requêtes et les codes de mise à jour XPath sont analysés sur le client. Pour bénéficier des fonctionnalités du modèle ou du code de mise à jour XPath dans SQLXML 4.0, utilisez Sqlxml4.dll.  
  
 L'illustration suivante montre l'architecture de la mise en forme XML côté client.  
  
 ![Architecture de mise en forme XML côté client.](../../../database-engine/dev-guide/media/clientsidexml.gif "Architecture de mise en forme XML côté client.")  
  
 Dans cet exemple, le client utilise le fournisseur SQLXMLOLEDB. Dans la chaîne de connexion, la propriété Fournisseur de données doit être définie sur SQLOLEDB. (Il s’agit de la seule valeur acceptée dans SQLXML 4,0.) La commande exécutée sur le client est envoyée au serveur. L'ensemble de lignes généré sur le serveur est envoyé au client. La mise en forme du document XML de l'ensemble de lignes est effectuée sur le client.  
  
 Dans SQLXML 4.0, le fournisseur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) ou le fournisseur SQLOLEDB peut être utilisé en tant que fournisseur de données. Vous pouvez éventuellement accéder à n'importe quelle source de données. Tant que la requête retourne un ensemble de lignes unique, la transformation XML peut être appliquée sur le client.  
  
  
