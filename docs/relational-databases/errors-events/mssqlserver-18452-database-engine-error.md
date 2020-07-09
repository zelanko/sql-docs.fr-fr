---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b26731ac3a8072c3b907b2ee6cf574ed636afacd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780662"
---
# <a name="mssqlserver_18452"></a>MSSQLSERVER_18452
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|18452|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOGON_INVALID_CONNECT|  
|Texte du message|Échec de l'ouverture de session pour l'utilisateur '%.*ls'. Il s’agit d’un compte de connexion SQL Server, qui ne peut pas être utilisé avec l’authentification Windows.%.\*ls.|  
  
## <a name="explanation"></a>Explication  
L'utilisateur a essayé de se connecter à l'aide d'informations d'identification qui ne peuvent pas être validées. Les causes possibles sont :  
  
-   La connexion peut être une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais le serveur accepte uniquement l'authentification Windows.  
  
-   Vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais la connexion utilisée n'existe pas sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   La connexion peut utiliser l'authentification Windows mais elle constitue un principal Windows non reconnu. Un principal Windows non reconnu signifie que la connexion ne peut pas être vérifiée par Windows. Cela peut être dû au fait que la connexion Windows s'effectue à partir d'un domaine non approuvé.  
  
Des problèmes similaires peuvent provoquer l'erreur 18456 moins spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré en mode Authentification mixte.  
  
Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existe.  
  
Si vous essayez de vous connecter à l'aide de l'authentification Windows, vérifiez que vous êtes correctement connecté au domaine approprié.  
  
