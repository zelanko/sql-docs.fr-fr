---
title: Planification de la capacité du serveur de sauvegarde
description: Cette feuille de planification de la capacité vous aide à déterminer la configuration requise pour un serveur de sauvegarde afin d’effectuer des opérations de sauvegarde et de restauration de base de données Data Warehouse parallèles. À utiliser pour créer votre plan pour l’achat de nouveaux ou l’approvisionnement de serveurs de sauvegarde existants.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 46dbdded5adf41a847f017cf4ee203597df13962
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401341"
---
# <a name="backup-server-capacity-planning-worksheet---parallel-data-warehouse"></a>Feuille de planification de la capacité du serveur de sauvegarde-Data Warehouse parallèles
Cette feuille de planification de la capacité vous aide à déterminer la configuration requise pour un serveur de sauvegarde afin d’effectuer des opérations de sauvegarde et de restauration de la base de données de SQL Server PDW. À utiliser pour créer votre plan pour l’achat de nouveaux ou l’approvisionnement de serveurs de sauvegarde existants.  
  
Cette feuille de calcul est un complément aux instructions fournies dans [acquérir et configurer un serveur de sauvegarde](acquire-and-configure-backup-server.md).  
  
## <a name="capacity-planning-worksheet-for-backup-servers"></a>Feuille de planification de la capacité pour les serveurs de sauvegarde  

### <a name="notes"></a>Notes  
  
1.  Cette feuille de calcul s’applique aux serveurs qui effectuent des opérations de sauvegarde et de restauration pour les bases de données PDW.  
  
2.  La seule façon de sauvegarder et de restaurer les bases de données PDW consiste à utiliser les commandes SQL BACKUP DATABASE et RESTORE DATABASE. Toutefois, une fois que les données de sauvegarde se trouvent sur votre serveur de sauvegarde, elles existent sous la forme d’un ensemble de fichiers Windows. Vous pouvez archiver les fichiers de sauvegarde à partir de votre serveur vers un autre emplacement de stockage à l’aide des méthodes de sauvegarde traditionnelles basées sur des fichiers Windows.  
  
### <a name="clipboard-iconmediaclipboard-iconpng-clipboard-icon-capacity-planning-worksheet"></a>![Icône du presse-papiers](media/clipboard-icon.png "Icône du presse-papiers") Feuille de planification de la capacité 
  
Imprimez cette feuille de calcul et remplissez-la avec vos propres exigences.  
  
|Composant|Condition requise|Renseignez cette colonne avec vos propres exigences|Recommandations|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Stockage|Nombre maximal d’octets que vous envisagez de stocker sur le serveur de sauvegarde à un moment donné.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Pour déterminer les besoins en stockage, déterminez la quantité de données que vous envisagez de stocker sur le serveur de sauvegarde à un moment donné.<br /><br />Les données de sauvegarde sont stockées sur le serveur de sauvegarde dans un format compressé. Les taux de compression des données dépendent des caractéristiques de vos données.<br /><br />Par exemple : comme estimation approximative, nous vous recommandons d’estimer un ratio de compression de 7:1 par rapport à la taille de vos données non compressées. Cela suppose qu’au moins 80% des données sont stockées dans des index ColumnStore en cluster. Par exemple, si vous avez 700 Go de données non compressées dans une base de données et que celles-ci sont stockées dans des index ColumnStore en cluster, vous pouvez estimer que la sauvegarde de base de données nécessite environ 100 Go.<br /><br />Si vous envisagez de disposer de plusieurs copies de sauvegardes de base de données sur le serveur de sauvegarde, vous devez prendre en compte ces dernières.<br /><br />Par exemple : Si vous envisagez de sauvegarder 10 bases de données qui contiennent chacune 5 to de données non compressées, les bases de données ont une taille combinée de 50 to. Si vous envisagez de sauvegarder ces 10 bases de données quotidiennement pendant 5 jours dans une ligne, la taille totale décompressée est de 250 to. En fonction du ratio de compression 7:1, vous aurez besoin de 250/7 = 35,7 to de stockage sur votre serveur de sauvegarde. Nous vous recommandons d’être prudent et de bénéficier d’une capacité supplémentaire de 30% pour tenir compte des variations et de la croissance.  Dans cet exemple, 46,6 to serait mieux.|  
|Réseau|Type de connexion réseau.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Déterminez le meilleur type de connexion réseau pouvant répondre à vos besoins en termes de taux de charge.<br /><br />Par exemple : InfiniBand ou 10 Gbit offre Ethernet fournira les vitesses de chargement optimales. 1 Gbit Ethernet limite les vitesses de chargement à 360 Go par heure ou moins.|  
|E/S|Octets par heure pour les écritures.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Pour l’écriture de sauvegardes sur disque, les vitesses d’écriture de 4 to par heure sont optimales.<br /><br />Par exemple : pour les lecteurs qui peuvent écrire 50 Mo/s, vous devez disposer d’au moins 24 disques, ainsi que d’autres éléments pour la mise en miroir ou la parité.<br /><br />Pour la capacité d’e/s, prenez en compte toutes les e/s qui se produisent sur le serveur de chargement. Si le serveur de chargement a un autre trafic d’e/s en plus des charges de données, telles que la réception de fichiers de données à partir d’un serveur ETL, les exigences d’e/s augmentent.|  
|UC|Nombre de Sockets.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|La réception et le stockage des fichiers de sauvegarde ne sont pas une application gourmande en ressources processeur.  Pour une configuration minimale, nous vous recommandons d’utiliser un serveur à 2 sockets fabriqué récemment.|  
|RAM|Go de mémoire qui permet à Windows de mettre en cache les fichiers pendant les chargements.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|La réception et le stockage des fichiers de sauvegarde nécessitent très peu de RAM sur le serveur de chargement.<br /><br />Pour déterminer les besoins en RAM, consultez votre installation de Windows Server et les applications tierces requises. Nous vous recommandons un minimum de 32 Go si vous n’avez pas de spécifications provenant d’autres sources.|  
  
Lorsque vous avez terminé de déterminer vos besoins en capacité, revenez à la rubrique [acquisition et configuration d’un serveur de chargement](acquire-and-configure-loading-server.md) pour planifier votre achat.  
  
## <a name="see-also"></a>Voir aussi  
[Sauvegarde et chargement de matériel](backup-and-loading-hardware.md)  
  
