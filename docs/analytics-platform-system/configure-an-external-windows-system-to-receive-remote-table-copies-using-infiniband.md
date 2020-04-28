---
title: Configurer Windows pour recevoir des copies de tables distantes
description: Décrit comment acheter et configurer un système non-appareil Windows connecté à l’aide du réseau InfiniBand pour une utilisation avec la fonctionnalité de copie de table distante en parallèle Data Warehouse. Le système Windows hébergera la base de données SQL Server qui reçoit la copie de la table distante à partir d’une base de données SQL Server PDW. Elle est achetée séparément de l’appareil et connectée au réseau de l’appliance InfiniBand.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 837d41cc929d90b2494682645127f985b5768546
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401315"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>Configurer un système Windows externe pour recevoir des copies de tables distantes à l’aide de InfiniBand-Parallel Data Warehouse
Décrit comment acheter et configurer un système non-appareil Windows connecté à l’aide du réseau InfiniBand pour une utilisation avec la fonctionnalité de copie de table distante dans SQL Server PDW. Le système Windows hébergera la base de données SQL Server qui reçoit la copie de la table distante à partir d’une base de données SQL Server PDW. Elle est achetée séparément de l’appareil et connectée au réseau de l’appliance InfiniBand.  
  
> [!NOTE]  
> La connexion via le réseau InfiniBand n’est pas requise pour l’utilisation de la copie de table distante. La connexion via le réseau Ethernet peut être effectuée si la bande passante Ethernet répond à vos besoins.  
  
Cette rubrique décrit l’une des étapes de configuration de la configuration de la copie des tables distantes. Pour obtenir la liste de toutes les étapes de configuration, consultez [copie de table distante](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>Avant de commencer  
Avant de configurer le système Windows externe, vous devez :  
  
1.  Achetez ou fournissez un système Windows qui recevra les copies distantes.  
  
2.  Branchez le système Windows dans le rack de contrôle (s’il y a suffisamment d’espace) ou suffisamment près de l’appareil pour pouvoir le connecter au réseau de l’appliance InfiniBand.  
  
3.  Achetez des câbles InfiniBand et une carte réseau InfiniBand auprès du fournisseur de matériel de votre appliance. Nous vous recommandons d’acheter une carte réseau avec deux ports pour la tolérance de panne lors de la réception des données exportées. Il est recommandé d’avoir une carte réseau à deux ports, mais elle n’est pas obligatoire.  
  
## <a name="configure-an-external-windows-system-to-receive-remote-table-copies"></a><a name="HowToWindows"></a>Configurer un système Windows externe pour recevoir des copies de tables distantes  
Pour configurer le système Windows externe, procédez comme suit :  
  
1.  Installez la carte réseau InfiniBand dans votre système Windows.  
  
2.  Connectez la carte réseau InfiniBand au commutateur InfiniBand principal dans le rack de contrôle à l’aide de câbles InfiniBand.  
  
3.  Installez et configurez le pilote Windows approprié pour la carte réseau InfiniBand.  
  
    Les pilotes InfiniBand pour Windows sont développés par OpenFabrics Alliance, un consortium de l’industrie des fournisseurs InfiniBand.  Le pilote approprié a peut-être été distribué avec votre adaptateur InfiniBand. Si ce n’est pas le cas, le pilote peut être téléchargé à partir de www.openfabrics.org.  
  
4.  Configurez l’adresse IP de chaque port de la carte. Les systèmes SMP sont requis pour utiliser des adresses IP statiques à partir d’une plage d’adresses réservée à cet effet. Configurez le premier port en fonction des paramètres suivants :  
  
    -   Adresse réseau IP : 172.16.132. x  
  
    -   Masque de sous-réseau IP : 255.255.128.0  
  
    -   Plage d’hôtes IP : 1-254  
  
    Pour les cartes réseau InfiniBand avec deux ports, configurez le deuxième port en fonction des paramètres suivants :  
  
    -   Adresse réseau IP : 172.16.132. x  
  
    -   Masque de sous-réseau IP : 255.255.128.0  
  
    -   Plage d’hôtes IP : 1-254  
  
5.  Si vous utilisez une carte à deux ports ou si plusieurs systèmes Windows externes sont connectés à un appareil, attribuez à chaque système un numéro d’hôte différent au sein de chaque sous-réseau IP.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
