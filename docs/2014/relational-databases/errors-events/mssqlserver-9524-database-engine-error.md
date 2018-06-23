---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8b64e4226d34c1e4541c1bac064e644c69491311
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143710"
---
# <a name="mssqlserver9524"></a>MSSQLSERVER_9524
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9254|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XMLERR_INVALID_COLUMNSET_XML|  
|Texte du message|Le contenu XML fourni n'est pas conforme au format XML requis pour les jeux de colonnes éparses.|  
  
## <a name="explanation"></a>Explication  
 Une tentative de modification d'un jeu de colonnes a été effectuée. Le contenu XML d'un jeu de colonnes doit satisfaire les restrictions de format d'un jeu de colonnes. Le format général d'un jeu de colonnes est le suivant :  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 Pour plus d'informations sur les jeux de colonnes, consultez la rubrique « Utilisation de jeux de colonnes » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Corrigez le format des données XML du jeu de colonnes mentionné dans l'instruction.  
  
  