---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cc805042bff7259a311ca3f2acf4c26db59381b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85031130"
---
# <a name="mssqlserver_50000"></a>MSSQLSERVER_50000
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|Version du produit|11.0|  
|ID de l’événement|50000|  
|Source de l’événement|SETUP|  
|Composant|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|Nom symbolique||  
|Texte du message|Erreur réseau lors de la tentative de lecture du fichier : '%. * ls'.|  
  
## <a name="explanation"></a>Explication  
 Tentative d'installation (ou de mise à jour) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sur un ordinateur où [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est déjà installé, et où l'installation existante provenait d'un fichier MSI qui a été renommé de sqlncli.msi.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, désinstallez la version existante de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Pour empêcher cette erreur, n'installez pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client à partir d'un fichier MSI qui n'est pas nommé sqlncli.msi.  
  
## <a name="internal-only"></a>Interne uniquement  
  
