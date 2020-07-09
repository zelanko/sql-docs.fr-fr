---
title: MSSQLSERVER_5515 | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5515 (Database Engine error)
ms.assetid: ccd793bc-ba5d-4782-8d72-731fd01fc177
author: MashaMSFT
ms.author: mathoma
robots: noindex,nofollow
ms.openlocfilehash: a9456aed02e9e1a2566bf0281dacd07f435af44b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728366"
---
# <a name="mssqlserver_5515"></a>MSSQLSERVER_5515
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|MSSQLSERVER|  
|ID de l’événement|5515|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|FS_OPEN_CONTAINER_FAILED|  
|Texte du message|Impossible d'ouvrir le répertoire conteneur « %.*ls » du fichier FILESTREAM. Le système d'exploitation a retourné le code d'état Windows 0x%x.|  
  
## <a name="explanation"></a>Explication  
Le répertoire conteneur spécifié pour le fichier FILESTREAM ne peut pas être ouvert.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour la cause de l'erreur, consultez le code d'état Windows spécifique.  
  
