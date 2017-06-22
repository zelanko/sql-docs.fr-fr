---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f872d7d0a2495e747ae0b3d63997f7270c585c53
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-native-client-error-mssqlserver50000"></a>Erreur de SQL Server Native Client MSSQLSERVER_50000
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|Version du produit|11.0|  
|ID d'événement|50000|  
|Source de l'événement|SETUP|  
|Composant|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|Nom symbolique||  
|Texte du message|Erreur réseau lors de la tentative de lecture du fichier : '%. * ls'.|  
  
## <a name="explanation"></a>Explication  
 Tentative d'installation (ou de mise à jour) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sur un ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est déjà installé, et où l'installation existante provenait d'un fichier MSI qui a été renommé de sqlncli.msi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, désinstallez la version existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour empêcher cette erreur, n'installez pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client à partir d'un fichier MSI qui n'est pas nommé sqlncli.msi.  
  
## <a name="internal-only"></a>Interne uniquement  
  
