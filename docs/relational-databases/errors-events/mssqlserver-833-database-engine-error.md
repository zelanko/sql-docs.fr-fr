---
title: MSSQLSERVER_833 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1d71b87d3927e2b79d2147099c50581a3687e32
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767828"
---
# <a name="mssqlserver_833"></a>MSSQLSERVER_833
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|833|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|BUF_LONG_IO|  
|Texte du message|SQL Server a rencontré %d occurrence(s) de requêtes d’E/S mettant plus de %d secondes à s’effectuer dans le fichier [%ls] de la base de données `[%ls] (%d)`.  Le descripteur de fichier du système d'exploitation est 0x%p.  Le décalage de la dernière E/S longue est : %#016I64x.|  
  
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
> L'accès au disque peut être ralenti par un antivirus. Pour augmenter la vitesse d'accès, excluez des analyses antivirus actives les fichiers de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont spécifiés dans le message d'erreur.  
  
Pour plus d’informations sur les erreurs d’E/S, consultez [Concepts de base des E/S de Microsoft SQL Server, chapitre 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) et l’article de la Base de connaissances disponible à l’adresse [https://support.microsoft.com/kb/897284/en-us](https://support.microsoft.com/kb/897284/en-us).  
  
