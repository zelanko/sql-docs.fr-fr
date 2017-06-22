---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8d7e546f593d1a54c2787da74cfe34502598a0b3
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|33027|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_CRYPTOPROV_CANTLOADDLL|  
|Texte du message|Impossible de charger le fournisseur de services de chiffrement '%.*ls' en raison d'une signature Authenticode non valide ou d'un chemin d'accès non valide. Recherchez d'autres défaillances dans les messages précédents.|  
  
## <a name="explanation"></a>Explication  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu utiliser le fournisseur de services de chiffrement répertorié dans le message d’erreur, parce que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu charger la DLL. Soit c'est le nom, soit c'est la signature Authenticode qui n'est pas valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez que le fichier existe et que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est autorisé à accéder à cet emplacement. Recherchez d'autres messages à ce sujet dans le journal des erreurs. Sinon, contactez le fournisseur de services de chiffrement pour plus d'informations.  
  

