---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2a0a00e5df34da8bf56cf92752e6bd0ea135d73
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67908520"
---
# <a name="mssqlserver_33027"></a>MSSQLSERVER_33027
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|33027|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_CRYPTOPROV_CANTLOADDLL|  
|Texte du message|Impossible de charger le fournisseur de services de chiffrement '%.*ls' en raison d'une signature Authenticode non valide ou d'un chemin d'accès non valide. Recherchez d'autres défaillances dans les messages précédents.|  
  
## <a name="explanation"></a>Explication  
SQL Server n’a pas pu utiliser le fournisseur de services de chiffrement indiqué dans le message d’erreur, parce qu’il n’a pas réussi à charger la DLL. Soit c'est le nom, soit c'est la signature Authenticode qui n'est pas valide.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez que le fichier existe et que SQL Server est autorisé à accéder à cet emplacement. Recherchez d'autres messages à ce sujet dans le journal des erreurs. Sinon, contactez le fournisseur de services de chiffrement pour plus d'informations.  
  
