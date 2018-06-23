---
title: MSSQLSERVER_945 | Microsoft Docs
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
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f06aed5f498ed67b7d9335cb37b62b1edb25327e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042722"
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|945|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DB_IS_SHUTDOWN|  
|Texte du message|La base de données '%.*ls' ne peut pas être ouverte, car des fichiers sont inaccessibles, ou la mémoire ou l'espace disque sont insuffisants.  Pour plus d’informations, consultez le journal des erreurs de SQL Server.|  
  
## <a name="explanation"></a>Explication  
 Il n'a pas été possible d'accéder à la base de données car il manque des fichiers ou d'autres ressources.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez le journal des erreurs pour trouver des informations supplémentaires sur les problèmes de mémoire, d'espace disque ou d'autorisation. Vérifiez l’emplacement des fichiers .mdf et .ndf de la base de données affectée et assurez-vous que le compte utilisé par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est autorisé à accéder à ces fichiers. Après avoir corrigé le problème, redémarrez la base de données en utilisant l'instruction ALTER DATABASE pour la mettre en ligne (ONLINE).  
  
  