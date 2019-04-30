---
title: Le chargement de la capacité du serveur planification - Analytique Platform System | Microsoft Docs
description: Cette feuille de planification de capacité vous aide à déterminer la configuration requise pour un serveur de chargement pour charger des données à Parallel Data Warehouse Analytique Platform System. »
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2f0efd7e0688496d5af7887431ca00ae683c874f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213389"
---
# <a name="loading-server-capacity-planning-worksheet-for-analytics-platform-system"></a>Le chargement de la feuille de planification de capacité de serveur pour l’Analytique Platform System
Cette feuille de planification de capacité vous aide à déterminer la configuration requise pour un serveur de chargement pour le chargement des données dans SQL Server PDW. Utilisez-le pour créer votre plan d’achat ou l’approvisionnement de chargement de serveurs existant.  
  
## <a name="worksheet-notes"></a>Notes de la feuille de calcul
  
1.  Cette feuille de calcul s’applique aux serveurs qui le chargement des données avec le **dwloader** outil de chargement de ligne de commande.  
  
2.  Pour charger des données avec Integration Services ou un outil de chargement de tiers, la configuration requise peut varier en fonction des différences dans le processus de chargement.  
  
3.  La plupart des exigences s’appliquent au chargement des fichiers de données compressé ou non ; toutes les différences dans les exigences sont indiquées en gras.  
  
## <a name="clipboardmediaclipboard-iconpng-clipboard-capacity-planning-worksheet"></a>![Presse-papiers](media/clipboard-icon.png "Presse-papiers") feuille de calcul Planification des capacités  
  
Imprimer cette feuille de calcul et la remplir avec vos propres exigences.  
  
|Composant|Condition requise|Remplissez cette colonne avec vos propres exigences|Recommandations|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Stockage|Nombre maximal d’octets que vous envisagez de stocker sur le serveur de chargement à une période de temps donnée.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Pour déterminer les besoins de stockage, déterminez la quantité de données vous souhaitez stocker sur le serveur de chargement à une période de temps donnée.  La capacité requise est pour charger les fichiers uniquement ; le système d’exploitation et les fichiers de charge doivent être sur baies de disques différents.<br /><br />Exemple : Si vous envisagez de charger 100 Go de données à partir du disque 3 fois chaque jour, mais ne supprime pas les fichiers de données jusqu'à la fin de la semaine, vous devez un 2,1 To minimum pour stocker les fichiers de données. Nous vous recommandons d’étant conservatrice et mise en route sur stockage de plus de 30 % pour prendre en compte les écarts et de croissance.  Pour cet exemple, 2,73 to d’espace de stockage serait préférable.|  
|Taux de charge|Nombre maximal d’octets par heure de données à charger dans PDW.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Il s’agit d’une estimation. Lors du calcul de cette exigence, supposons que les fichiers sont déjà sur le serveur de chargement, et que les autres conditions de chargement sont aussi bon que possibles.<br /><br />Exemple : Aucun nécessaire de tenir compte des compressibilité des données dans la mesure où dwloader envoie toujours ne décompressé les données à l’empaquetage. Pas nécessaire de tenir compte des conversions de types de données et la taille de la table de destination.|  
|Réseau|Type de connexion réseau.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Déterminer le meilleur type de connexion de réseau pour vos exigences de taux de charge.<br /><br />Exemple : InfiniBand ou 10 GB Ethernet fournira les taux de chargement optimal. 1 Gb Ethernet limitera les taux de charge à 360 Go par heure ou moins.|  
|E/S|Octets par heure pour les lectures et écritures.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Pour charger des données, dwloader doit lire toutes les données à partir du disque avant de les envoyer à PDW.<br /><br />Chaque serveur de chargement impossible de charger plus rapidement que l’appliance peut recevoir des données à partir de toutes les sources de chargement des données. Pour réaliser des économies, planifiez les e/s de lecture de capacité pour le chargement afin qu’il ne dépasse pas la capacité de charge de l’appliance.<br /><br />Exemple :<br />PDW reçoit et charge les données dans une appliance de rack de 1 à un taux maximal de 1,8 To par heure. Pour une appliance dotée des racks 2 ou plus, le taux de charge maximale est de 3,6 To par heure.<br /><br />Si vous envisagez de charger à partir de plusieurs serveurs de chargement en même temps, les exigences d’e/s pour chaque serveur de chargement sera inférieure à quand un seul serveur effectue tout le chargement.<br /><br />Exemple : Un serveur de chargement peut charger un maximum de 1,8 To par heure pour un dispositif de rack de 1. Deux serveurs de chargement impossible chacun charger en même temps 900 Go par heure à un dispositif de rack de 1. Les niveaux supérieurs de l’accès concurrentiel peuvent réduire l’efficacité et le débit maximal.<br /><br />Pour la capacité d’e/s, prendre en compte toutes les e/s qui se produisent sur le serveur de chargement. Si le chargement du serveur a tout autre trafic d’e/s en plus des chargements de données, telles que la réception des fichiers de données à partir d’un serveur ETL, les exigences d’e/s augmentera.<br /><br />Pour les données compressées, les exigences d’e/s varient selon le taux de compression de données. dwloader lit les données compressées et il décompresse ensuite avant de les envoyer à PDW. Plus le taux de compression, les moins de données le serveur de chargement doit lire à partir du disque.<br /><br />Exemple : Si le taux de charge requis est 1,8 To par heure, et les données sont stockées sur le serveur de chargement avec la compression de 2:1, le chargement du serveur doit uniquement lire des 900 Go par heure à partir du disque au lieu de 1,8 To. Un taux de compression 3:1 signifie que le chargement du serveur doit lire 600 Go par heure à partir du disque.|  
|Unité centrale|Nombre de sockets.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|Pour le chargement des données non compressées, dwloader n’est pas une application sollicitant beaucoup le processeur.  Au minimum, nous recommandons à l’aide d’un serveur 2 sockets fabriqués récemment.<br /><br />Pour le chargement des données compressées, vous avez besoin de suffisamment de puissance du processeur de décompresser les données avant de les envoyer à PDW. dwloader pouvez exécuter 10 threads actifs en même temps. Si vous envisagez de charger simultanément les 10 fichiers compressés, nous recommandons que le serveur a au moins une UC de 10 cœurs ou deux processeurs 6 cœurs.|  
|RAM|Go de mémoire permettant à Windows en cache les fichiers au cours de charge.|![Icône de crayon](media/pencil-icon.png "icône de crayon")|dwloader utilise très peu de RAM sur le serveur de chargement. Pour des performances, Windows utilise la mémoire pour mettre en cache les fichiers de chargement après leur lecture à partir du disque.<br /><br />Pour déterminer la mémoire RAM requise, reportez-vous à votre installation de Windows Server et des exigences d’application tiers 3e. Nous recommandons un minimum de 32 Go si vous n’avez pas de configuration requise à partir d’autres sources.<br /><br />Pour les données compressées, RAM plus rapide est utile, car il s’accélère la décompression.|  
  
## <a name="see-also"></a>Voir aussi  
[Obtenir et configurer un serveur de chargement](acquire-and-configure-loading-server.md)  
[dwloader du chargeur de ligne de commande](dwloader.md)  
  
