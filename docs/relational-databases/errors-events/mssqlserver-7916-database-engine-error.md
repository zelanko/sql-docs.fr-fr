---
title: MSSQLSERVER_7916 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eadb07e1f7add72d181546a3c1a74c9bbf6ca406
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85693964"
---
# <a name="mssqlserver_7916"></a>MSSQLSERVER_7916
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|7916|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_REPAIR_RECORD|  
|Texte du message|Réparation : enregistrement supprimé pour l’ID d’objet O_ID, ID d’index I_ID, ID de partition PN_ID, ID d’unité d’allocation A_ID (type TYPE), à la page P_ID, emplacement S_ID. Les index seront reconstruits.|  
  
## <a name="explanation"></a>Explication  
Ceci est un message d'information de REPAIR qui indique que l'enregistrement spécifié a été supprimé de la page.  
  
## <a name="user-action"></a>Action de l'utilisateur  
None  
  
