---
title: MSSQLSERVER_17053 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17053 (Database Engine error)
ms.assetid: e0a01f3d-d0aa-4c38-8bcc-82e59de50512
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 09a09ba19aa51777d06f9392c04617f27298693b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver17053"></a>MSSQLSERVER_17053
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17053|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|OS_ERROR|  
|Texte du message|%ls : erreur du système d'exploitation %ls.|  
  
## <a name="explanation"></a>Explication  
Une erreur générique du système d'exploitation s'est produite.  L'état résultant est indéfini.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Habituellement cette erreur apparaît conjointement avec une autre erreur et doit servir à diagnostiquer cet échec. Les exemples peuvent inclure des échecs de lecture ou d'écriture des données ou des fichiers journaux, des opérations en lecture/écriture du Registre, ou d'autres échecs Win32API inattendus.  
  
