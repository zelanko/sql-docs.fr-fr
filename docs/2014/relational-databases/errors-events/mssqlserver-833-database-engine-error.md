---
title: MSSQLSERVER_833 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b827814c5cc6b8659f52c0ff07cde9c3600235a4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48071619"
---
# <a name="mssqlserver833"></a>MSSQLSERVER_833
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|833|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|BUF_LONG_IO|  
|Texte du message|SQL Server a rencontré %d occurrence (s) de demandes d’e/s mettant plus de %d secondes à effectuer dans le fichier [%ls] de la base de données`[%ls] (%d)`.  Le descripteur de fichier du système d'exploitation est 0x%p.  Le décalage de la dernière E/S longue est : %#016I64x.|  
  
## <a name="explanation"></a>Explication  
 Ce message indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a émis une demande de lecture ou d'écriture à partir du disque et que la demande a mis plus de 15 secondes à retourner un résultat. Cette erreur est signalée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et indique un problème avec le sous-système d'E/S.  
  
### <a name="possible-causes"></a>Causes possibles  
 Cette erreur peut être due à des problèmes de performances du système, à des erreurs matérielles, à des erreurs de microprogramme, à des problèmes de pilote de périphérique ou à l'intervention d'un pilote de filtre dans le processus d'E/S.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Essayez de résoudre le problème en recherchant dans le journal des événements système d'éventuels messages d'erreur liés au matériel. Examinez également les journaux spécifiques au matériel s'ils sont disponibles.  
  
 Utilisez l'Analyseur de performances pour consulter les compteurs suivants :  
  
-   **Moyenne disque s/transfert**  
  
-   **Longueur moyenne de la file d’attente du disque**  
  
-   **Longueur actuelle de la file d’attente du disque**  
  
 Par exemple, la durée **Moyenne disque s/transfert** sur un ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est généralement inférieure à 15 millisecondes. Si la valeur **Moyenne disque s/transfert** augmente, cela indique que le sous-système d’E/S ne parvient pas parfaitement à suivre la demande d’E/S.  
  
> [!NOTE]  
>  L'accès au disque peut être ralenti par un antivirus. Pour augmenter la vitesse d'accès, excluez des analyses antivirus actives les fichiers de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont spécifiés dans le message d'erreur.  
  
 Pour plus d’informations sur les erreurs d’E/S, consultez [Concepts de base des E/S de Microsoft SQL Server, chapitre 2](http://go.microsoft.com/fwlink/?LinkId=69370) et l’article de la Base de connaissances disponible à l’adresse [http://support.microsoft.com/kb/897284/en-us](http://support.microsoft.com/kb/897284/en-us).  
  
  
