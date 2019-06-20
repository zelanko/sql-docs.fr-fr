---
title: Planification des capacités de serveur de sauvegarde - Parallel Data Warehouse | Microsoft Docs
description: Cette feuille de planification de capacité vous aide à déterminer la configuration requise pour un serveur de sauvegarde pour la sauvegarde de base de données de Parallel Data Warehouse et les opérations de restauration. Utilisez-le pour créer votre plan d’achat nouvelle ou mise en service sauvegarde des serveurs existants.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 500bebab375a0d0b94032a1855af3844bc2e6fa7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63295058"
---
# <a name="backup-server-capacity-planning-worksheet---parallel-data-warehouse"></a>Feuille de planification capacité serveur de sauvegarde - Parallel Data Warehouse
Cette feuille de planification de capacité vous aide à déterminer la configuration requise pour un serveur de sauvegarde pour la sauvegarde de base de données SQL Server PDW et opérations de restauration. Utilisez-le pour créer votre plan d’achat nouvelle ou mise en service sauvegarde des serveurs existants.  
  
Cette feuille de calcul est un complément des instructions dans [obtenir et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md).  
  
## <a name="capacity-planning-worksheet-for-backup-servers"></a>Feuille de planification de capacité pour les serveurs de sauvegarde  

### <a name="notes"></a>Remarques  
  
1.  Cette feuille de calcul s’applique aux serveurs que vous allez effectuer des opérations de sauvegarde et de restauration pour les bases de données PDW.  
  
2.  La seule façon pour sauvegarder et restaurer des bases de données PDW consiste à utiliser les commandes de base de données de sauvegarde et restauration de base de données SQL. Toutefois, une fois les données de sauvegarde sur le serveur de sauvegarde, il existe un ensemble de fichiers de Windows. Vous pouvez archiver les fichiers de sauvegarde à partir de votre serveur vers un autre emplacement de stockage à l’aide de Windows basés sur fichier méthodes de sauvegarde traditionnelles.  
  
### <a name="clipboard-iconmediaclipboard-iconpng-clipboard-icon-capacity-planning-worksheet"></a>![Icône de Presse-papiers](media/clipboard-icon.png "icône Presse-papiers") feuille de planification de capacité 
  
Imprimer cette feuille de calcul et la remplir avec vos propres exigences.  
  
|Composant|Condition requise|Remplissez cette colonne avec vos propres exigences|Recommandations|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Stockage|Nombre maximal d’octets que vous envisagez de stocker sur le serveur de sauvegarde sur une période de temps donnée.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Pour déterminer les besoins de stockage, déterminez la quantité de données vous envisagez de stocker sur le serveur de sauvegarde sur une période de temps donnée.<br /><br />Les données de sauvegarde sont stockées sur le serveur de sauvegarde dans un format compressé. Taux de compression de données varie selon les caractéristiques de vos données.<br /><br />Exemple : Comme une estimation approximative, nous vous recommandons d’estimation d’un taux de compression de 7:1 par rapport à la taille de vos données non compressées. Cela suppose d’au moins 80 % des données sont stocké dans les index columnstore en cluster. Par exemple, si vous avez 700 Go de données non compressées dans une base de données et il est stocké dans les index columnstore en cluster, puis vous pouvez estimer que la sauvegarde de base de données devez environ 100 Go.<br /><br />Si vous prévoyez d’avoir plusieurs copies de sauvegardes de base de données sur le serveur de sauvegarde, vous devez prendre en compte.<br /><br />Exemple : Si vous envisagez de sauvegarder 10 bases de données qui contiennent chacun des 5 To de données non compressées, les bases de données ont une taille combinée de 50 To. Si vous envisagez de sauvegarder ces tous les jours de 10 bases de données pendant 5 jours dans une ligne, la taille totale est de 250 To. En tenant compte un taux de compression de 7:1, vous devez 250 / 7 = 35,7 To de stockage sur le serveur de sauvegarde. Nous vous recommandons d’étant conservatrice et mise en route sur 30 % de capacité supplémentaire à tenir compte des variances et de croissance.  Dans cet exemple, to 46,6 serait préférable.|  
|Réseau|Type de connexion réseau.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Déterminer le meilleur type de connexion de réseau capable de répondre aux besoins de votre taux de charge.<br /><br />Exemple : InfiniBand ou taux de charge de 10 Gbit Ethernet fournira l’optimal. Ethernet de 1 Gbit limitera les taux de charge à 360 Go par heure ou moins.|  
|E/S|Octets par heure pour les écritures.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Pour l’écriture des sauvegardes sur disque, de 4 To par heure vitesses d’écriture sont optimales.<br /><br />Exemple : Pour les lecteurs qui peuvent écrire des 50 Mo/s, vous devez au moins 24 disques, ainsi que pour la mise en miroir ou parité.<br /><br />Pour la capacité d’e/s, prendre en compte toutes les e/s qui se produisent sur le serveur de chargement. Si le chargement du serveur a tout autre trafic d’e/s en plus des chargements de données, telles que la réception des fichiers de données à partir d’un serveur ETL, les exigences d’e/s augmentera.|  
|Unité centrale|Nombre de sockets.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Recevoir et stocker des fichiers de sauvegarde ne sont pas une application sollicitant beaucoup le processeur.  Au minimum, nous recommandons à l’aide d’un serveur 2 sockets fabriqués récemment.|  
|RAM|Go de mémoire permettant à Windows en cache les fichiers au cours de charge.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Recevoir et stocker des fichiers de sauvegarde requièrent très peu de RAM sur le serveur de chargement.<br /><br />Pour déterminer la mémoire RAM requise, reportez-vous à votre installation de Windows Server et des exigences d’application tiers 3e. Nous recommandons un minimum de 32 Go si vous n’avez pas de configuration requise à partir d’autres sources.|  
  
Lorsque vous avez terminé la détermination de vos besoins en capacité, revenez à la [obtenir et configurer un serveur de chargement](acquire-and-configure-loading-server.md) rubrique pour planifier votre achat.  
  
## <a name="see-also"></a>Voir aussi  
[Sauvegarde et chargement de matériel](backup-and-loading-hardware.md)  
  
