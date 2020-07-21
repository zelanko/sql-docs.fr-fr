---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c82132c02376176b5e524f42aadcd343cc40d68b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553082"
---
# <a name="mssqlserver_9524"></a>MSSQLSERVER_9524
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|9254|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XMLERR_INVALID_COLUMNSET_XML|  
|Texte du message|Le contenu XML fourni n'est pas conforme au format XML requis pour les jeux de colonnes éparses.|  
  
## <a name="explanation"></a>Explication  
 Une tentative de modification d'un jeu de colonnes a été effectuée. Le contenu XML d'un jeu de colonnes doit satisfaire les restrictions de format d'un jeu de colonnes. Le format général d'un jeu de colonnes est le suivant :  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 Pour plus d'informations sur les jeux de colonnes, consultez la rubrique « Utilisation de jeux de colonnes » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Corrigez le format des données XML du jeu de colonnes mentionné dans l'instruction.  
  
  
