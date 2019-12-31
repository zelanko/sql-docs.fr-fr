---
title: Chargement de la planification de la capacité du serveur
description: Cette feuille de planification de la capacité vous aide à déterminer la configuration requise pour un serveur de chargement pour le chargement de données dans le Data Warehouse parallèle d’Analytics Platform System.»
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 7dded8c79495d0bdc684927f4875a93c3160c1bf
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401031"
---
# <a name="loading-server-capacity-planning-worksheet-for-analytics-platform-system"></a>Chargement de la feuille de planification de la capacité du serveur pour Analytics Platform System
Cette feuille de planification de la capacité vous aide à déterminer la configuration requise pour un serveur de chargement pour le chargement de données dans SQL Server PDW. À utiliser pour créer votre plan d’achat ou de configuration de serveurs de chargement existants.  
  
## <a name="worksheet-notes"></a>Notes de la feuille de calcul
  
1.  Cette feuille de calcul s’applique aux serveurs qui chargent des données avec l’outil de chargement en ligne de commande **dwloader** .  
  
2.  Pour le chargement de données avec Integration Services ou un outil de chargement tiers, les exigences peuvent varier en fonction des différences dans le processus de chargement.  
  
3.  La plupart des exigences concernent le chargement de fichiers de données compressés ou non compressés. les différences en termes de spécifications sont indiquées en gras.  
  
## <a name="clipboardmediaclipboard-iconpng-clipboard-capacity-planning-worksheet"></a>![Presse-papiers](media/clipboard-icon.png "Presse-papiers") Feuille de planification de la capacité  
  
Imprimez cette feuille de calcul et remplissez-la avec vos propres exigences.  
  
|Composant|Prérequis|Renseignez cette colonne avec vos propres exigences|Recommandations|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Stockage|Nombre maximal d’octets que vous envisagez de stocker sur le serveur de chargement à un moment donné.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Pour déterminer les besoins en stockage, déterminez la quantité de données que vous envisagez de stocker sur le serveur de chargement à un moment donné.  Les besoins en capacité ne concernent que les fichiers de charge ; le système d’exploitation et les fichiers de charge doivent se trouver sur des baies de disques différentes.<br /><br />Par exemple : Si vous envisagez de charger 100 Go de données à partir du disque 3 fois par jour, mais ne supprimez pas les fichiers de données jusqu’à la fin de la semaine, vous devez disposer d’un minimum de 2,1 to pour stocker les fichiers de données. Nous vous recommandons d’être prudent et de bénéficier d’environ 30% de stockage supplémentaire pour tenir compte des variations et de la croissance.  Pour cet exemple, 2,73 to d’espace de stockage sont préférables.|  
|Vitesse de chargement|Nombre maximal d’octets par heure de données à charger dans PDW.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Il s’agit d’une estimation. Lors du calcul de cette exigence, supposez que les fichiers se trouvent déjà sur le serveur de chargement et que d’autres conditions de chargement sont aussi efficaces que possible.<br /><br />Par exemple : il n’est pas nécessaire de factoriser la compression des données, car dwloader envoie toujours des données non compressées au PDW. Il n’est pas nécessaire de factoriser les conversions de types de données et la taille de la table de destination.|  
|Réseau|Type de connexion réseau.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Déterminez le meilleur type de connexion réseau pour vos besoins en termes de taux de charge.<br /><br />Par exemple : InfiniBand ou 10 GB Ethernet fournit les vitesses de chargement optimales. 1 GB Ethernet limite la vitesse de chargement à 360 Go par heure ou moins.|  
|E/S|Octets par heure pour les lectures et les écritures.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Pour charger des données, dwloader doit lire toutes les données à partir du disque avant de les envoyer à PDW.<br /><br />Chaque serveur de chargement ne peut pas charger les données plus rapidement que l’appliance ne peut recevoir des données de toutes les sources de chargement. Pour économiser de l’argent, planifiez la capacité de lecture des e/s pour le chargement afin qu’il ne dépasse pas la capacité de chargement de l’appliance.<br /><br />Par exemple :<br />PDW reçoit et charge les données dans un appareil à 1 rack à une vitesse maximale de 1,8 to par heure. Pour une appliance avec 2 racks ou plus, la vitesse de chargement maximale est de 3,6 to par heure.<br /><br />Si vous envisagez de charger à partir de plusieurs serveurs de chargement en même temps, les exigences d’e/s de chaque serveur de chargement seront inférieures à celles qu’un serveur effectue tout le chargement.<br /><br />Par exemple : un serveur de chargement peut charger jusqu’à 1,8 to par heure pour un appareil à 1 rack. Deux serveurs de chargement peuvent chacun charger simultanément 900 Go par heure dans un appareil à 1 rack. Les niveaux d’accès concurrentiel plus élevés peuvent réduire l’efficacité et le débit maximal.<br /><br />Pour la capacité d’e/s, prenez en compte toutes les e/s qui se produisent sur le serveur de chargement. Si le serveur de chargement a un autre trafic d’e/s en plus des charges de données, telles que la réception de fichiers de données à partir d’un serveur ETL, les exigences d’e/s augmentent.<br /><br />Pour les données compressées, les exigences d’e/s dépendent du taux de compression des données. dwloader lit les données compressées, puis les décompresse avant de les envoyer à PDW. Plus le taux de compression est élevé, moins le serveur de chargement devra lire les données sur le disque.<br /><br />Par exemple : si la vitesse de chargement requise est de 1,8 to par heure et que les données sont stockées sur le serveur de chargement avec la compression 2:1, alors le serveur de chargement doit uniquement lire 900 Go par heure à partir du disque au lieu de 1,8 to. Un ratio de compression de 3:1 signifie que le serveur de chargement doit lire 600 Go par heure à partir du disque.|  
|UC|Nombre de Sockets.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|Pour le chargement de données non compressées, dwloader n’est pas une application gourmande en ressources processeur.  Pour une configuration minimale, nous vous recommandons d’utiliser un serveur à 2 sockets fabriqué récemment.<br /><br />Pour le chargement de données compressées, vous devez disposer de suffisamment de puissance de processeur pour décompresser les données avant de les envoyer à PDW. dwloader peut exécuter 10 threads actifs à la fois. Si vous envisagez de charger 10 fichiers compressés simultanément, nous recommandons que le serveur dispose d’au moins un processeur de 10 cœurs ou de deux processeurs à 6 cœurs.|  
|RAM|Go de mémoire qui permet à Windows de mettre en cache les fichiers pendant les chargements.|![Icône de crayon](media/pencil-icon.png "Icône de crayon")|dwloader utilise très peu de RAM sur le serveur de chargement. Pour des performances optimales, Windows utilise de la mémoire pour mettre en cache les fichiers de chargement après les avoir lus sur le disque.<br /><br />Pour déterminer les besoins en RAM, consultez votre installation de Windows Server et les applications tierces requises. Nous vous recommandons un minimum de 32 Go si vous n’avez pas de spécifications provenant d’autres sources.<br /><br />Pour les données compressées, une RAM plus rapide est utile, car elle accélère la décompression.|  
  
## <a name="see-also"></a>Voir aussi  
[Obtenir et configurer un serveur de chargement](acquire-and-configure-loading-server.md)  
[Chargeur de ligne de commande dwloader](dwloader.md)  
  
