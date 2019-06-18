---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f336c64ffc0d044fa0f7282f3c87451483353879
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914950"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|MSSQLSERVER|  
|ID d'événement|21862|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21862|  
|Texte du message|Les colonnes FILESTREAM ne peuvent pas être publiées dans une publication à l'aide d'une méthode de synchronisation 'database snapshot' ou 'database snapshot character'.|  
  
## <a name="explanation"></a>Explication  
 Étant donné qu’il est impossible d’accéder aux données FILESTREAM par le biais d’un instantané de base de données, l’agent d’instantané ne peut pas lire les données FILESTREAM quand le paramètre *database snapshot* ou *database_snapshot_character* est spécifié pour la méthode de synchronisation de la publication.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez la méthode de synchronisation de publication en sélectionnant un paramètre autre que *database snapshot* ou *database_snapshot_character*, ou excluez simplement la colonne FILESTREAM de la publication.  
  
  
