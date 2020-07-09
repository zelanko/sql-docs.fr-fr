---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d9eb240ffe26a91b59413468f54cf5b2376779e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780923"
---
# <a name="mssqlserver_17053"></a>MSSQLSERVER_17053
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|17053|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|OS_ERROR|  
|Texte du message|%ls : Erreur système %ls.|  
  
## <a name="explanation"></a>Explication  
Une erreur générique du système d'exploitation s'est produite.  L'état résultant est indéfini.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Habituellement cette erreur apparaît conjointement avec une autre erreur et doit servir à diagnostiquer cet échec. Les exemples peuvent inclure des échecs de lecture ou d'écriture des données ou des fichiers journaux, des opérations en lecture/écriture du Registre, ou d'autres échecs Win32API inattendus.  
  
