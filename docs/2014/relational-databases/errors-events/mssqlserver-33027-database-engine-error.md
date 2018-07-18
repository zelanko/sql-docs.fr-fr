---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f6ba0947d3966295e34c22f7069a1a31b9a6137
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425358"
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
  
  
