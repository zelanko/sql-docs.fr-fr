---
title: Configurer Windows pour recevoir une copie de la table distante - Parallel Data Warehouse | Microsoft Docs
description: Décrit comment acheter et configurer un système de Windows non-appliance connecté via le réseau InfiniBand pour une utilisation avec la fonctionnalité de copie de table distante dans Parallel Data Warehouse. Le système Windows hébergera la base de données SQL Server qui reçoit la copie de la table distante à partir d’une base de données SQL Server PDW. Il est vendu séparément à partir de l’appliance et connecté au réseau InfiniBand appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 428dc5b4edda91f60a09a52c0326f881f257b32c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961309"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>Configurer un système Windows externe pour recevoir une copie de table distante à l’aide d’InfiniBand - Parallel Data Warehouse
Décrit comment acheter et configurer un système de Windows non-appliance connecté via le réseau InfiniBand pour une utilisation avec la fonctionnalité de copie de table distante dans SQL Server PDW. Le système Windows hébergera la base de données SQL Server qui reçoit la copie de la table distante à partir d’une base de données SQL Server PDW. Il est vendu séparément à partir de l’appliance et connecté au réseau InfiniBand appliance.  
  
> [!NOTE]  
> Connexion via le réseau InfiniBand n’est pas requise pour utiliser la copie de la table distante. Connexion via le réseau Ethernet peut être effectuée si la bande passante Ethernet répond à vos besoins.  
  
Cette rubrique décrit l’une des étapes de configuration pour la configuration de copie de la table distante. Pour obtenir la liste de toutes les étapes de configuration, consultez [copie de Table distante](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>Avant de commencer  
Avant de configurer le système Windows externe, vous devez :  
  
1.  Acheter ou fournir un système Windows qui recevra les copies à distance.  
  
2.  Monter en rack le système Windows dans le rack de contrôle (s’il existe suffisamment d’espace) ou suffisamment proches pour l’appliance afin que vous pouvez vous connecter au réseau InfiniBand appliance.  
  
3.  Acheter InfiniBand câbles et un adaptateur de réseau InfiniBand auprès de votre fournisseur de matériel d’appliance. Nous vous recommandons d’acheter une carte réseau avec deux ports pour une tolérance de panne lors de la réception des données exportées. Une carte réseau de deux ports est recommandée, mais n’est pas obligatoire.  
  
## <a name="HowToWindows"></a>Configuration d’un système Windows externe pour recevoir une copie de la Table distante  
Pour configurer le système Windows externe, utilisez les étapes suivantes :  
  
1.  Installez l’adaptateur de réseau InfiniBand dans votre système Windows.  
  
2.  Se connecter à la carte réseau InfiniBand pour le commutateur InfiniBand principal dans le rack de contrôle à l’aide de câbles de InfiniBand.  
  
3.  Installez et configurez le pilote Windows approprié pour la carte réseau InfiniBand.  
  
    Les pilotes InfiniBand pour Windows sont développés par OpenFabrics Alliance, un consortium d’entreprises de fournisseurs de InfiniBand.  Le pilote correct peut ont été distribué avec la carte réseau InfiniBand. Si ce n’est pas le cas, le pilote peut être téléchargé à partir de www.openfabrics.org.  
  
4.  Configurer l’adresse IP pour chaque port sur la carte. Les systèmes SMP sont requis pour utiliser des adresses IP statiques à partir d’une plage d’adresses réservées à cet effet. Configurer le premier port en fonction des paramètres suivants :  
  
    -   Adresse IP du réseau : 172.16.132.x  
  
    -   Masque de sous-réseau IP : 255.255.128.0  
  
    -   Plage d’IP hôte : 1-254  
  
    Pour les cartes réseau InfiniBand avec deux ports, configurez le second port en fonction des paramètres suivants :  
  
    -   Adresse IP du réseau : 172.16.132.x  
  
    -   Masque de sous-réseau IP : 255.255.128.0  
  
    -   Plage d’IP hôte : 1-254  
  
5.  Si une carte à deux ports est utilisée, ou plusieurs systèmes Windows externes sont connectés à un matériel, vous pouvez affecter chaque système un numéro de hôte différent dans chaque sous-réseau IP.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
